# 👋 Hi, I’m Shufan Pang (`pangshufan`)

**Senior Platform & Systems Architect | Geospatial & Agentic Infrastructure | IoT Connectivity & Simulation | Deep-Dive Troubleshooting**

I am a systems-first architect and problem solver with **16+ years** of experience designing, rescuing, and operating mission-critical platforms across **Earth Observation (Remote Sensing), Industrial IoT, Telecom, and Enterprise Data Infrastructure**.

My core strength lies at the intersection of **distributed control planes, binary/network protocol engineering, Linux/OS internals, and zero-trust data pipelines**—especially in air-gapped, resource-constrained, or high-pressure field environments where standard playbooks fail and end-to-end ownership is non-negotiable.

📍 **Open to Relocation (Visa Sponsorship) & Global Remote** · 📫 [pangoutwise@gmail.com](mailto:pangoutwise@gmail.com)

---

## 🏗️ Signature Platform Architectures

### 1. Intelligent Remote Sensing & Zero-Trust Agentic Platform
Architected a four-plane geospatial intelligence platform unifying PB-scale satellite imagery processing, OGC publishing, and enterprise LLM tool orchestration:
- **Cloud-Native Geospatial Data Lake:** Built around **STAC v1.0.0 (`pgstac`)**, **Cloud-Optimized GeoTIFF (COG)** HTTP Range streaming with client-side WebGL rendering, **PostGIS**, **GeoServer**, and **SeaweedFS/S3**—supporting optical (Sentinel-2, Himawari-9 AHI) and SAR (NISAR, ALOS-2) pipelines.
- **Zero-Trust Credential Isolation for AI Agents:** Eliminated credential leakage risks in LLM prompts/tool calls by designing a **Java 21 / Spring Cloud Resource Grant Center** that issues short-lived, `RS256`-signed JWS capability packages (`STS` tokens, scoped DB/GeoServer grants), paired with 8 client-side pre-flight policy checks and strict outbound `host:port` SSRF allowlists.
- **Long-Running Compute State Machine (`WAITING_CREDENTIALS`):** Solved the mismatch between short-lived security tokens and multi-hour heavy raster jobs via non-destructive job suspension and automated background grant renewal/resumption.
- **Context-Bounded Agent SDK & Immutable Lineage:** Early adopter of **MCP (Model Context Protocol)** patterns; engineered a zero-native-dependency agent SDK using semantic skill routing (capping active tool schemas per turn and cutting async polling payloads by **>90%**) alongside tamper-evident **SHA-256 S3 metadata lineage DAGs**.

### 2. High-Concurrency IoT Connectivity & Fleet Simulation (`IoT Studio`)
End-to-end engineering from carrier/enterprise device ingestion to deterministic protocol simulation:
- **20,000+ Device Burst Governance (<3s SLA):** Re-architected gateway binary protocol parsing, tuned Linux kernel TCP/FD queues, and corrected Nginx L4 load-balancing local-bias weights to absorb synchronized hourly reporting bursts—achieving years of **zero-touch production operation** and isolating third-party RF chipset defects via behavioral packet analysis.
- **IoT Access Architecture (Patent Application):** Distilled field bottlenecks from massive heterogeneous device onboarding and connection scheduling into a formal invention disclosure / patent application.
- **`IoT Studio` Multi-Protocol Fleet Simulator:** Designed a desktop simulation workbench supporting **TCP/TLS, UDP, MQTT 3.1.1/5, HTTP/HTTPS, and CoAP**, decoupled from version-pinned codec plugins running in isolated subprocesses. Enforces production-grade semantics: **idempotent retries** (preserving request ID, sequence, timestamp, and nonce), non-blocking full-duplex auto-replies, and four-stage delivery telemetry (transport write vs. ACK match vs. business acceptance vs. logical completion).
- **Hardware Protocol Reverse Engineering ([`ar844-client`](https://github.com/pangshufan/ar844-client) / [`ar844-usb-driver`](https://github.com/pangshufan/ar844-usb-driver)):** Captured and reverse-engineered undocumented industrial USB HID sound-level meter protocols via Wireshark into a cross-platform desktop acquisition & acoustic analytics suite (P10/L90 noise-floor windowing, udev rules, automated Windows/Linux/macOS CI).

---

## 🔥 Selected War Stories: Deep-Dive Troubleshooting & Global Delivery

- **4 Hours vs. 1 Year — Cross-Layer Latency Root Cause:** Resolved a year-long intermittent 30s database connection stall on ARM Linux (`Oracle RAC` / `JDBC`) in 4 hours by isolating a minimal reproducer, ruling out packet loss via `tcpdump`, and pinpointing `Inet6AddressImpl` IPv6 DNS resolution blocking via `jstack`.
- **100x Storage I/O Reversal:** Overturned a vendor's costly CPU-expansion recommendation on a stalled data platform by proving random disk I/O saturation (`iostat -x` `%util > 90%`) and leading an SSD tier migration that delivered **100x throughput** at a fraction of the budget.
- **Surgical Bare-Metal & Database Disaster Recovery:** Reconstructed production environments in hours after catastrophic private-cloud system-disk loss, performing file-level **MySQL InnoDB** tablespace and redo-log recovery with **zero data loss** without snapshots.
- **Cross-Border Telecom Rescue (Thailand, Indonesia, Sri Lanka):**
  - Rescued a delayed flagship ISP **FTTH / SIP Voice / Multicast IPTV** rollout in Thailand; halted an un-STP'd L2 broadcast storm within 5 minutes and delivered automated OSS/BSS provisioning (`TL1/XML`).
  - Broke multi-team deadlocks by diagnosing L7 HTTP WAF false-positives dropping `MQTT` handshakes and `SNMP` PDU fragmentation exceeding device MTU limits; achieved **100x speedup** on legacy carrier collection pipelines via algorithmic hash-index refactoring.
  - Authored pixel-accurate physical rack & cabling "digital twins" ([`Server_Topo-DigitalTwin-like.pdf`](resources/Server_Topo-DigitalTwin-like.pdf)) to bridge spoken-language barriers, enabling local field crews to wire complex server/SAN/switch/F5 topologies with **zero communication friction and zero cabling errors**.
- **Pragmatic ROI in Constrained Environments:** Built offline ARM RPM software supply chains for air-gapped networks, zero-install in-memory ETL engines for locked-down banking migrations (ICBC, **12x faster**), and CPU-only `FastText + AutoML` microservices where GPUs were unavailable.

---

## 📂 Selected Public Repositories

> **Engineering Workflow Note:** My native foundation is **systems architecture, Java/Spring microservices, SQL/databases, Linux internals, and network protocols**. For cross-platform desktop utilities, host agents, and polyglot SDKs (`Python` / `Go`), I practice **spec-driven, AI-augmented engineering**—authoring strict protocol state machines, memory/security bounds, and edge-case test contracts while leveraging AI to accelerate multi-language implementation and CI packaging.

- **[`ar844-client`](https://github.com/pangshufan/ar844-client)** & **[`ar844-usb-driver`](https://github.com/pangshufan/ar844-usb-driver)** — Wireshark reverse-engineered USB HID driver and cross-platform desktop acoustic monitor (SQLite time-windowed percentiles, HID timeout recovery, multi-OS GitHub Actions).
- **[`file-sync-server-sftp`](https://github.com/pangshufan/file-sync-server-sftp)** — Multi-tenant SFTP server with a custom v1/v2 incremental file-sync protocol (`AsyncSSH` + `PySide6`) and companion **Java client SDK**.
- **[`linux-minitor`](https://github.com/pangshufan/linux-minitor)** — Outbound-only Linux (`/proc`, `/sys`, `cgroups`) & Windows host observability system over **gRPC + mTLS** with built-in PKI certificate issuance and `SQLite WAL` / `PostgreSQL` storage.
- **[`local-communication`](https://github.com/pangshufan/local-communication)** — Zero-broadcast, stealth-by-default LAN messaging & zero-copy large-file streaming tool featuring `Ed25519`/HMAC pairing and strict memory-watermarked ring buffers.

---

## 🛠️ Technical Capabilities

- **Architecture & Control Plane (Native Core):** `Java (8–21)` · `Spring Boot / Spring Cloud` · `REST / gRPC / Protobuf` · `Zero-Trust Auth (JWS / RS256 / mTLS / STS / OS Keyring)` · `System & Protocol State Machines`
- **Geospatial & Data Engineering:** `STAC (pgstac)` · `COG` · `GDAL / PROJ / Rasterio` · `PostGIS` · `GeoServer (WMS/WFS)` · `Oracle RAC` · `MySQL (InnoDB Internals)` · `PostgreSQL` · `S3 / SeaweedFS` · `Kafka` · `Redis`
- **IoT, Networking & Linux Systems:** `Linux Internals & Kernel Tuning (x86 / ARM / OpenWrt)` · `TCP/IP` · `MQTT 3.1.1/5` · `CoAP` · `USB HID` · `Wireshark / tcpdump` · `OLT/ONT / SIP / Multicast IPTV / VLAN / SAN`
- **AI-Augmented & Pragmatic AI Engineering:** `MCP & Agent Skill Routing` · `Spec-Driven Polyglot Prototyping (Python / Go / PySide6)` · `Lightweight MLOps (Conda-Pack / FastText)` · `Shell / SQL / PL/SQL`

---

## 🌌 Beyond Engineering: Systems Thinking & Hard Sci-Fi

- **Visual Engineering Across Languages:** See [`Server_Topo-DigitalTwin-like.pdf`](resources/Server_Topo-DigitalTwin-like.pdf) — a pixel-level physical server, disk-array, switch, and F5 cabling blueprint created to achieve zero-error datacenter deployment across language barriers.
- **[Seeds of Life: Planetary Self-Operations (`essays/seeds-of-life-planetary-self-operations.md`)](essays/seeds-of-life-planetary-self-operations.md):** A hard sci-fi & systems-philosophy monograph distilling 16+ years of unattended infrastructure instincts into a speculative worldview—modeling biosphere evolution and industrial civilization as a **zero-OpEx, self-healing planetary system** governed by decentralized fault tolerance, objective alignment risks, and long-horizon ROI.
