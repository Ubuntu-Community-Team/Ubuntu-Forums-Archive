---
title: "Hibernate PowerEdge servers with Ubuntu 16.04"
date: 2017-02-03
forum: General Help
---

### Post by fabianborg on 2017-02-03
I am aware that servers are built to run 24/7, but for security and power saving reasons, I would like to power manage my servers being: Dell PowerEdge 1950 Gen II, PE 2950 Gen II and PE r710 all running Ubuntu 16.04 lts. The CPUs have been configured from BIOS to be power managed by the OS.

The idea is that the servers will hibernate after 20 minutes of idle time and wake with wake-on-lan magic packets. 

I have searched the net for a solution but all I found was withdrawn dependencies or implementations for laptop/pc use, none for servers.

SWAP size is 64gb on each server. 

Any ideas?

---

