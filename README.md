# Bandwidth Measurement and Analysis in SDN
**Name:** Suraj C D   
**SRN:** PES2UG24AM165   
**Subject:** Computer Networks (UE24CS252B)

## 1. Problem Statement
The goal of this project is to measure and analyze network bandwidth (throughput) and latency in a Software Defined Network (SDN) environment. The project evaluates how a Ryu controller manages flow rules in an Open vSwitch (OVS) topology.

## 2. Setup & Topology
- **OS:** Lubuntu 20.04 (LTS)
- **Controller:** Ryu (OpenFlow 1.3)
- **Mininet Topology:** Single switch connected to 3 hosts.
- **Commands used:**
  - Controller: `ryu-manager ryu.app.simple_switch_13`
  - Mininet: `sudo mn --topo single,3 --controller remote --switch ovs,protocols=OpenFlow13`

## 3. Results and Analysis
### A. Functional Correctness (Connectivity)
- **Test:** `pingall`
- **Observation:** 0% packet loss. The controller successfully handled `packet_in` events and installed forwarding rules.

### B. Performance Observation (Bandwidth)
- **Test:** `iperf h1 h2`
- **Result:** Throughput recorded at **10.1 Gbits/sec**.
- **Analysis:** This high throughput indicates minimal overhead from the controller once flow rules are established in the data plane.

### C. SDN Flow Rules
- **Command:** `ovs-ofctl dump-flows s1`
- **Logic:** The controller implements a Learning Switch mechanism, mapping MAC addresses to ports.

## 4. Screenshots
![Pingall Results](./screenshots/pingall_ss.png)
![Iperf Results](./screenshots/iperf_ss.png)
![Flow Table](./screenshots/flow_table_ss.png)
