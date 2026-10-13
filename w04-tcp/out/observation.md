Task 1 — Reliable Delivery



I chose stop-and-wait because it is simple to implement and handles lost ACKs through retransmission.



For 2,000 bytes, the minimum is 250 packets, but my program sent 323 packets (1.29 times the minimum).



Packet loss required retransmissions, while sequence numbers prevented duplicate packets from corrupting the received data.





Task 2 — TCP Measurement



Packets 1–3 show SYN, SYN-ACK and ACK. The initial sequence numbers were 2613271311 and 3269249088, randomized to avoid confusion with old connections. MSS values were 1460/1360 bytes, window scales were 256/8192, and both sides supported SACK.



The server advertised a scaled receive window of 131072 bytes, while I observed only 458 bytes in flight. The receive window did not seem to be the limit at that moment.



Home Wi-Fi had a median of 139.18 Mbps (53% spread, 11.3 ms handshake), compared with 36.99 Mbps on mobile hotspot (117% spread, 45.4 ms handshake). Wireless conditions and congestion may explain the variation, while longer RTT increases handshake and TCP slow-start overhead.





Task 3 — Congestion Control



The fixed window had slightly higher goodput, but it caused 37.4% packet loss and many retransmissions, making it a worse sender for a shared network.



I limited my window to 24 packets, close to the 20-packet link capacity plus a small queue. This reduced the average queue to 3.8 packets.



With a gentler 0.8 backoff, my algorithm achieved 975.2 goodput (99% of baseline) with 0% loss, at the cost of slightly lower throughput than the baseline.

