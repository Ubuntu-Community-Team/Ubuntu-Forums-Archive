---
title: "booting from old HDDs"
date: 2016-07-19
forum: General Help
---

### Post by popi2 on 2016-07-19
Hello ubuntu forum,

I retrieved a couple of hard disk drives from old laptops and computers I had laying  around the house. I'd like to boot them properly using a hard drive dock. 
I'm currently running ubuntu 16.04 kernel 4.4.0-31-generic on a Yoga 500-14ACL. The HDDs all run ubuntu, not sure about the releases or kernels. 

I've been trying to gain some understanding about the whole process from google, but I'm not sure I understand what's at stake; I keep reading about OEM, re-installing drivers, wiping current hdd etc etc.

Could somebody do a ELI5 for me please?

---

### Post by sudodus on 2016-07-19
Welcome to the Ubuntu Forums :-)

I think most adapters and external boxes nowadays are made to connect SATA drives to USB 3 ports, but there are alternatives. You can find for example

- a 'USB to SATA & IDE cable' which is actually an adapter to connect a SATA or IDE (PATA) drive via USB to a computer,

- a 'USB / eSATA to SATA enclosure' which can be a box (enclosure) or an open adapter to connect a SATA drive via USB or eSATA to a computer.

The adapters and boxes that I have tested work for booting as well as for storage. If connected via USB you select it in the same way as you would select a USB pendrive for booting. If connected via eSATA you select it in the same way as you would select a SATA drive for booting (in different ways depending on the UEFI/BIOS system).

In a similar way it is possible to connect flash memory cards (SD and other types) via adapters. I have found many card adapters that you can boot from, and others that only work for storage in systems that are already booted from another drive.

See these links and links from them for more details:

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

-o-

Finally, while installed linux systems can boot from external drives, Windows is made to boot only when installed in internal drives. Only the Windows *installer* can boot from DVD or USB. There are also Windows pre-installation environment systems, that you can make from a (legal) copy of Windows.

---

### Post by oldfred on 2016-07-19
If you can plug drives in, then this can tell you a lot about the other installs.

Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

