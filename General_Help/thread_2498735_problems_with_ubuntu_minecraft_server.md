---
title: "problems with ubuntu minecraft server"
date: 2024-06-25
forum: General Help
---

### Post by socksinbed343 on 2024-06-25
**_Problem:_**

I have been trying to make a minecraft server on ubuntu 24.04 but whenever I have tried to access the server on my computer I get the error: [I]connection timed out: getsockopt.


[/I]**_General Info:_**

I am trying to access the server on a windows 11 computer.

I AM able to access the server when my computer is on the same internet as the server.

I AM NOT able to access the server when I am on a different internet (my friend has tried and I have also tried while using a personal hotspot).

My server is connected to the router via ethernet.

I have already done port forwarding on the router for the 25565 port and I have also set a static IP address for the ubuntu server.

I have disabled both public and private windows firewalls and also worked with the inbound rules on windows to enable the 25565 port.

I have disabled the firewalls on the ubuntu server and allowed the 25565 server on ubuntu.

I have worked slightly with exceptions for java programs on windows.


If there are any solutions that I should try or any solutions I should revisit to solve my problem please tell me.

---

### Post by currentshaft on 2024-06-25
Port forwarding is a terrible idea, because now everyone in the world can access your computer at that port. And if the software you're running on it is vulnerable, you've potentially just handed someone control over your PC.

Rent a virtual server, use SSH to forward your local port to it, then you and your friends can connect to the server over an encrypted connection and treat it as if it were on your LAN.

---

