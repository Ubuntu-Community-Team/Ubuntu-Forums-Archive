---
title: "How can I install e4rat on Lubuntu?"
date: 2017-10-02
forum: General Help
---

### Post by ten1ten on 2017-10-02
e4rat doesn't show up in software center.  Although I download e4rat, I don't know how to install it.  I'm a newbie and could use some basic steps in getting it installed.  Thanks in advance.

---

### Post by HermanAB on 2017-10-02
If a program is not in the repo, then it is not supported.  

E4rat will likely not do what you want and may damage your system.

---

### Post by ten1ten on 2017-10-02
In that case, what is recommended for me to have a faster bootup time?  The machine runs great once it's booted, but it takes over 2 minutes to boot.

---

### Post by ian-weisser on 2017-10-02
Which release of Ubuntu? Which flavor?

---

### Post by ten1ten on 2017-10-02
Lubuntu 17.04.

---

### Post by ian-weisser on 2017-10-02
Open a terminal.
Do the following commands:
```
systemd-analyze blame
systemd-analyze critical-chain
```
Copy-and-paste the entire output of both commands into your reply.
Use [code] tags to keep the formatting. The formatting is very helpful.

---

### Post by ten1ten on 2017-10-03
[IMG]https://drive.google.com/open?id=0B3yMwsjc7xKfbk9fRm92My1JUmM[/IMG]a1@1:~$ systemd-analyze blame
         11.454s dev-sda6.device
          8.768s keyboard-setup.service
          7.820s systemd-udevd.service
          7.703s systemd-sysctl.service
          5.712s NetworkManager-wait-online.service
          2.402s NetworkManager.service
          2.188s accounts-daemon.service
          2.139s ModemManager.service
          2.063s resolvconf.service
          1.987s snapd.service
          1.204s gpu-manager.service
          1.100s grub-common.service
          1.040s polkit.service
           983ms systemd-tmpfiles-setup-dev.service
           933ms systemd-modules-load.service
           906ms bluetooth.service
           838ms colord.service
           757ms sys-kernel-debug.mount
           756ms dev-hugepages.mount
           707ms dev-mqueue.mount
           658ms upower.service
           572ms ufw.service
           546ms apparmor.service


Please see attachment below for a1@1:~$ systemd-analyze critical-chain

---

### Post by ian-weisser on 2017-10-03
Pro Tip: Search the forum for how to use [code] tags. Much faster and easier than screenshots.

Your sysinit.target is taking an extraordinarily long time.  1min 30 sec! Mine is a mere 10 sec.

Next time you reboot, note the time.
Then scroll back in /var/log/syslog for the kernel boot messages at that time. Look for a long delay between messages (more than 3 or 4 seconds). Show us the block of messages before and after that delay.

---

### Post by HermanAB on 2017-10-04
BTW, why do you reboot at all?  Use suspend/resume.  There is almost no good reason to shut down and reboot.

---

