---
title: "Disk space is reduced after /usr/lib/systemd/systemd-journal error"
date: 2023-05-02
forum: General Help
---

### Post by smallmx on 2023-05-02
I have the following problem after installing ubuntu 22.04.2 when using it it throws me the following error /usr/lib/systemd/systemd-journal error
 after sending the report the hard drive (ssd) starts reducing its size until it is full on the full capacity in less than two hours and 
the same happens with version 23.04

---

### Post by TheFu on 2023-05-04
The wording of the issue is confusing.  Is the SSD total amount getting smaller ... like blocks are failing?

Or, could you mean that log files are just growing and using more storage because there is an issue that hasn't been corrected?
Did you look at the system logs to determine the root cause and fix it?  Often, taking the error message from the logs and putting that into google will provide a solution.

Please clarify, if you'd like help.

---

### Post by smallmx on 2023-05-05
Exactly the system logs are growing due to a device error apparently, checking the system logs I could find the following pcieport 0000:00:1c.6: device[8086:a296] error status/mask=00000001/00002000 and pcieport 0000 :00:1c.6: PCIe bus error: severity=fixed, type=physical layer, (Receiver ID),
 but can't find the device causing the error

---

### Post by smallmx on 2023-05-05
Exactly the system logs are growing due to a device error apparently, checking the system logs I could find the following pcieport 0000:00:1c.6: device[8086:a296] error status/mask=00000001/00002000 and pcieport 0000 :00:1c.6: PCIe bus error: severity=fixed, type=physical layer, (Receiver ID), but can't find the device causing the error

---

### Post by Holger_Gehrke on 2023-05-05
```

lspci -tv

```
will give you a list of all PCI and PCI express devices. [8086:a296] is an Intel PCI express host, the interesting piece of hardware is something connected to that at port address 1c.6. During the search for this information I came across several complaints similar to yours but with different port addresses. It usually is some network / WLAN controller that produces the problem ...

Holger

---

### Post by smallmx on 2023-05-06
Thanks, I was able to identify the device that causes the problem if it is network /WLAN, and investigated and recommend grub to add the following in grub: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pcie_aspm=off"
 I don't know how recommendable it is, I'm new to ubuntu, could you guide me on whether it is a good option or recommend a site where I can see how to update the driver of my wifi card  TP-WN781ND (RTL8188EE)

---

