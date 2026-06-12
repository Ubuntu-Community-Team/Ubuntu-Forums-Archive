---
title: "Boot Up Issue"
date: 2013-11-04
forum: General Help
---

### Post by cessanfrancisco on 2013-11-04
Sometimes when I try to boot up Ubuntu 13.10, on my Lenovo Z580, I get a purple screen for a very long time (5-10 mins) until I do a hard reset by pressing and holding down the power button.  Usually after that it boots up ok.

Has anyone else had this issue?  Does anyone know of a fix?

Thanks in advance.

---

### Post by mof689 on 2013-12-20
Unfortunately I don't have a solution for this problem but can confirm that I have exactly the same issue with my HP Pavillion ZV5000 and Ubuntu 12.04 LTS. I have noticed that when booting hangs it is either when detecting PCMCIA cardbus or when is validating the swap area on the harddisk. SMART data on my hard drive as well as independent verification of hard drive via BIOS all confirm 100% healthy drive. I am using GRUB_CMDLINE_LINUX_DEFAULT="reboot=bios start_pcmcia=false" in GRUB configuration file but although subjectively it has improved I still run into this issue. I also have tried GRUB boot repair and have played with some options but still the issue is present. Ubuntu Linux is the only OS on my machine.

---

