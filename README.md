# CyberOps Wireshark Labs

Network analysis labs completed on the **Cisco CyberOps Workstation** virtual machine
(VirtualBox, Mininet, Wireshark 2.5.1, tcpdump). The reports are written in French.

## Labs
| # | Lab | Topic | Report |
|---|---|---|---|
| 1 | 5.3.7 | Introduction to Wireshark: Mininet topology, ICMP capture and analysis | [PDF](Lab1_5.3.7_Intro_Wireshark.pdf) |
| 2 | 8.2.8 | Ethernet II frames: MAC addresses, ARP broadcast, local vs remote traffic | [PDF](Lab2_8.2.8_Ethernet_Frames.pdf) |
| 3 | 10.6.7 | HTTP vs HTTPS: credentials in clear text vs TLS encryption | [PDF](Lab3_10.6.7_HTTP_vs_HTTPS.pdf) |
| 4 | 21.2.12 | Telnet vs SSH: clear-text session vs encrypted session | [PDF](Lab4_21.2.12_Telnet_vs_SSH.pdf) |

## Key findings
1. **Local vs remote traffic:** when a host pings a machine on another network, the IP destination is the final host, but the Ethernet destination MAC is the default gateway's. MAC addresses only matter inside one LAN.
2. **ARP and frames:** an ARP broadcast (`ff:ff:ff:ff:ff:ff`) finds the MAC address needed to build the Ethernet header. The first 3 bytes of a MAC identify the vendor (OUI).
3. **HTTP vs HTTPS:** an HTTP login form sends the username and password in clear text, readable in a capture. With HTTPS, Wireshark only shows TLS "Encrypted Application Data". HTTPS proves the connection is encrypted, not that the site is trustworthy.
4. **Telnet vs SSH:** the Telnet stream shows the password in clear text. SSH negotiates keys and then encrypts everything, so SSH should replace Telnet for remote administration.

## Skills practiced
Wireshark display filters (`icmp`, `http`, `http.request.method == "POST"`, `tcp.port==443`, `ssh`),
Follow TCP Stream, tcpdump (`-i`, `-s 0`, `-w`), Mininet topologies, packet analysis of Ethernet, IPv4,
ICMP, ARP, HTTP, TLS, Telnet and SSH.

## Notes
- These are my own write-ups. The original lab instructions (Cisco Networking Academy) are not included.
- All captures were made inside an isolated virtual machine. The credentials visible in the reports are the
  default lab VM account and the public test site `demo.testfire.net`, which is intentionally vulnerable.

**Author:** Radhia Hamed
