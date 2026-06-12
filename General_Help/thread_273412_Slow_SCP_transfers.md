---
title: "Slow SCP transfers?"
date: 2006-10-08
forum: General Help
---

### Post by Daniel15 on 2006-10-08
Hi everyone,
 Recently, I've been noticing some slow speeds during SCP copying of files. Here's what I'm using:

**PC 1**
[LIST]
[*]Windows XP
[*]Realtek RTL-8139 network card (100Base-TX)
[*] WinSCP3 (SCP client)
[/LIST]

**PC 2**
[list]
[*] Ubuntu Linux 6.06
[*] Broadcom network card (listed by lspci as: ```
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```)
[*] OpenSSH
[/list]

I'm transferring some files from PC 1 to PC 2, and it is going really slow. Over the 100 Mb/s network, transfer speeds barely reach 300 KB/s. Does anyone know what's causing the slow speeds? I know that SCP would incur some overhead, but I wouldn't expect it to be *this* slow...

---

### Post by dcstar on 2006-10-08
> **Daniel15 said:**
> Hi everyone,
 Recently, I've been noticing some slow speeds during SCP copying of files. Here's what I'm using:

**PC 1**
[LIST]
[*]Windows XP
[*]Realtek RTL-8139 network card (100Base-TX)
[*] WinSCP3 (SCP client)
[/LIST]

**PC 2**
[list]
[*] Ubuntu Linux 6.06
[*] Broadcom network card (listed by lspci as: ```
0000:03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
```)
[*] OpenSSH
[/list]

I'm transferring some files from PC 1 to PC 2, and it is going really slow. Over the 100 Mb/s network, transfer speeds barely reach 300 KB/s. Does anyone know what's causing the slow speeds? I know that SCP would incur some overhead, but I wouldn't expect it to be *this* slow...

Check that the XP machine's Windows Firewall isn't causing problems, see if unencrypted transfers work at better rates.

---

### Post by viz_e on 2006-10-27
Same problem here. After edgy update I do not get more than 1.2 Mb/s between two linux machines (little CPU load). Before edgy it was a factor 10 better.

Is it something I can try?

---

