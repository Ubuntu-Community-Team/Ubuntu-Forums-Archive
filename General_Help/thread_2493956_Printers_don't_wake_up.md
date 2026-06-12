---
title: "Printers don't wake up"
date: 2023-12-31
forum: General Help
---

### Post by ckrles on 2023-12-31
Hi, I've upgraded to Ubuntu 22.04Lts from 20.04 Lts. I have a problem with two printers: Brother HL-3140cw and Brother MFC-L3770cdw on a wifi network. I have correctly set them up and they both print and scan fine, but after a while or a day, I try to print and they are not available, nor in the printers sections in general settings, nor in the printing dialog of different software. I have to manually power them off and back on. Then they are immediately detected. I thought they could go into deep sleep and Ubuntu 22.04 Lts couldn't wake them up, but even after printing something from my phone, Ubuntu wouldn't see them. How could I solve it? It didn't happen on Ubuntu 20.04 Lts.

In case it has something to do with printer sharing, I'm running samba in my pc to share a couple of folders.
If I type the printers ip in firefox I can acces the set up, which indicate automatic power off in 1h. At the beginning I thought that could be the answer, but it doesn't make sense, since other devices (android phones, ipad, mac pc) in my network can access it. So I guess it must be something related to my new 22.04 Lts install. Any ideas?

Thank you very much.

---

### Post by SeijiSensei on 2023-12-31
I have a Brother HL-3170cdw which I access over the network. It's hard wired to my router and has a static IP address. I can print to it from 22.04 machines in various rooms, and it wakes when a job is sent. Notice I'm not using the printer's built-in wifi but an Ethernet cable. DK if that matters.

---

### Post by MAFoElffen on 2023-12-31
In a different perspective -- I have an Espon ET-2760, that is connected to my Workstation and is also setup separately to my WiFi Network. In it's setup, it goes into a standby power savings mode... That mode is a bit quarky.

If I print to it via the USB from my Workstation it wakes right up.

If I want to print to it from WiFi, I walk up to it in the back room and press the OK button and it wakes up. It doesn't want to wake up sometimes, just from WiFi... A pain, but I just thought of it as normal for "that printer".

If I'm lazy, I just remote into my Workstation and wake it up by accessing any function of it.

---

### Post by ckrles on 2024-01-06
Sorry, I' a bit late to answer. So, no idea about what causes the non wake up? In my previous install, Ubuntu 20.04 Lts, the printers worked correctly out the box.

---

### Post by SeijiSensei on 2024-01-06
Let me be more explicit. Is the printer hard-wired into your network, or is it running wifi? As I said, I never have a problem with my Brother, connected directly to the router with an Ethernet cable, waking up. Have you tried that alternative?

---

### Post by pqwoerituytrueiwoq on 2024-01-07
I have a HL-L2360DW and have the same experience as SeijiSensei using a wired connection, my Mom has a HLL2300D (USB only) and it is a PITA every time i print i have to hit the power button i think it shuts itself off after hour or something silly like that

---

### Post by him610 on 2024-01-07
I have an older Brother MFC7360N and a Dell 1700N that are connected by Cat 5 cable to the local network.
Several (Xubuntu 2204.3) computers are also connected by Cat 5 cable to the local network; however, one laptop (Xubuntu 2204.3) is connected ***wirelessly*** through the network to the printers.
Both printers have assigned stable local addresses.
No issues with any of the computers or laptop printing to either of the networked computers.
Occasionally, the Brother MFC7360N somehow gets locked up with an HP All-in-One running Win10 that requires a power cycle on the printer.

---

