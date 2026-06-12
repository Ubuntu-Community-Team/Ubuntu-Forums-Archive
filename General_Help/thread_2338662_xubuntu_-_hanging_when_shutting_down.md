---
title: "xubuntu - hanging when shutting down"
date: 2016-09-30
forum: General Help
---

### Post by makem2 on 2016-09-30
Recently xubuntu has hung occasionally after I select 'shut down'. It just stops, showing the logo and revolving circle. The only way to shut it down is to remove the power.

I wonder if anyone can suggest a solution please.

```

makem@ssdTOSH:~$ inxi Fxz
CPU~Dual core Intel Core i7-5500U (-HT-MCP-) speed/max~1038/3000 MHz Kernel~4.4.0-38-generic x86_64 Up~8 min Mem~1394.8/15961.6MB HDD~1240.3GB(2.3% used) Procs~214 Client~Shell inxi~2.2.35  
makem@ssdTOSH:~$grub-install --version
grub-install (GRUB) 2.02~beta2-36ubuntu3.2
makem@ssdTOSH:~$ cat /proc/version
Linux version 4.4.0-38-generic (buildd@lgw01-58) (gcc version 5.4.0 20160609 (Ubuntu 5.4.0-6ubuntu1~16.04.2) ) #57-Ubuntu SMP Tue Sep 6 15:42:33 UTC 2016
makem@ssdTOSH:~$ls /usr/bin/*session
/usr/bin/ck-launch-session  /usr/bin/dbus-run-session  /usr/bin/xfce4-session

```

---

### Post by #&amp;thj^% on 2016-09-30
There are motherboards that have an option "WOL" or Wake-on-LAN

> Wake-on-LAN (WoL) is an Ethernet or Token ring computer networking standard that allows a computer to be turned on or awakened by a network message.
A physical Wake-on-LAN connector featured on the IBM PCI Token-Ring Adapter 2 (the large white connector).

The message is usually sent by a program executed on another computer on the same local area network. It is also possible to initiate the message from another network by using subnet directed broadcasts or a WOL gateway service. Equivalent terms include wake on WAN, remote wake-up, power on by LAN, power up by LAN, resume by LAN, resume on LAN and wake up on LAN. In case the computer being awakened is communicating via Wi-Fi, a supplementary standard called Wake on Wireless LAN (WoWLAN) must be employed.[1]


If you do not use that feature...or even try for testing... disable it.
I have seen where this motherboard "Intel DZ77GA-70K" is one that fix will work on.

---

### Post by makem2 on 2016-09-30
> **1fallen said:**
> There are motherboards that have an option "WOL" or Wake-on-LAN


If you do not use that feature...or even try for testing... disable it.
I have seen where this motherboard "Intel DZ77GA-70K" is one that fix will work on.

All Wake On whaterver are disabled and have never been enabled.

The shutdown just hung again. I am concerned that this seems to be happening more often. Tomorrow I must make another backup in case the HD gets corrupted.

Is there a command line command to check the HD for integrity and fix errors?

Edit:
```

makem@ssdTOSH:~$ sudo fsck /dev/sda1
[sudo] password for makem: 
fsck from util-linux 2.27.1
fsck.fat 3.0.28 (2015-05-16)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
1) Remove dirty bit
2) No action
? 
1
fsck from util-linux 2.27.1
fsck.fat 3.0.28 (2015-05-16)
/dev/sda1: 8 files, 7289/477876 clusters
makem@ssdTOSH:~$ 

```

No help there. System not shutting down every time now.

---

### Post by makem2 on 2016-09-30
I forgot to mention and am not sure if it makes any difference:

This laptop has two drives, an SSD on which is sda and sdb, a HD on which there is an old install of xubuntu which does not boot now and a dual boot Windows 10.

I had intended removing the redundant xubuntu at some stage.

The machine came with a single HD and I installed xubuntu with the already installed Windows 10. At a later date I added an SSD drive in a caddy in the DVD drive bay and put a fresh install of  xubuntu on that.

Edit: I have realised the fsck error I made by using sda1

---

### Post by #&amp;thj^% on 2016-10-01
I do not think the amount of hard drives matters as I have 3 hard drives that I boot.
Try using (Booting) an older kernel to see if some updates have caused the new anomaly.
This has been problematic since early in development.
Some said disconnecting from the Net using the Network applet helped.

---

### Post by makem2 on 2016-10-01
I got an error report n a reboot about plymouthd crashing.

Have sent in a report.so will wait a while before reverting to 14.04 which appears to be the only advanced option I have on boot.

---

### Post by makem2 on 2016-10-04
Errors have stopped and the machine shuts down correctly now. I have no idea why the change.

---

