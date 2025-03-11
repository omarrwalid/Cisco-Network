# Network Design using Cisco Packet Tracer

This project demonstrates the design and implementation of a scalable and efficient network using Cisco Packet Tracer. The network connects multiple routers, switches, and PCs, using **RIP** for routing and **DHCP** for automatic IP assignment.

## Features

- **Three routers** connected in series.
- **Switches** connected to the routers and PCs.
- **RIP (Routing Information Protocol)** for automatic route updates.
- **Static IP Addressing** between routers for controlled communication.
- **DHCP** for automatic IP assignment to PCs.

## Installation and Setup

1. **Add Routers**:
   - Place three routers (R1, R2, R3) in Cisco Packet Tracer.
   - Use serial connections to link them: 
     - R1 to R2.
     - R2 to R3.

2. **Configure Static IP Addresses Between Routers**:
   - For R1-R2 connection, set:
     - R1: `192.168.11.1/24`
     - R2: `192.168.11.2/24`
   - For R2-R3 connection, set:
     - R2: `192.168.12.1/24`
     - R3: `192.168.12.2/24`

3. **Add Switches and PCs**:
   - Connect **Switch1** to R2 and **Switch2** to R3.
   - Attach two additional switches to each main switch (Switch1 and Switch2).
   - Connect 5 PCs to each additional switch.

4. **Configure RIP on the Routers**:
   - On each router, access the CLI and enable RIP:
     ```bash
     enable
     configure terminal
     router rip
     version 2
     network 192.168.11.0
     exit
     ```
   - Repeat this configuration on R2 and R3 with the appropriate networks.

5. **Configure DHCP**:
   - On R1, configure a DHCP pool for the PCs connected to Switch1:
     ```bash
     ip dhcp pool PC_Network
     network 192.168.31.0 255.255.255.0
     default-router 192.168.31.1
     exit
     ```
   - Repeat on R3 for the PCs connected to Switch2.

6. **Connect and Test**:
   - Use straight-through cables to connect routers to their respective switches.
   - Test that the PCs are receiving IP addresses from DHCP.
   - Use the `ping` command to verify connectivity between PCs.

7. **Verify Network Connectivity**:
   - Use the `ping` command from one PC to another PC across the network to ensure the network is functioning:
     ```bash
     ping 192.168.31.x
     ```

## Key Protocols

- **RIP**: A simple distance-vector routing protocol used for routing between the routers.
- **DHCP**: Provides automated IP assignment to end devices.

## Advantages

- **Scalability**: Easily add more PCs or devices without reconfiguring the entire network.
- **Automated IP Management**: Using DHCP reduces the need for manual IP configuration.
- **Efficient Routing**: RIP updates routing tables automatically.

## Limitations

- **RIP Scalability**: Limited to a maximum of 15 hops, making it unsuitable for larger networks.
- **Static IP Complexity**: Requires manual configuration between routers, which can be error-prone.

## Conclusion

This project successfully demonstrates the design and implementation of a scalable network with dynamic IP assignment and automated routing updates. Challenges included configuring RIP and troubleshooting IP address issues, but the network functions efficiently after setup.

![Network Topology](path/to/your/network_topology_image.png)
