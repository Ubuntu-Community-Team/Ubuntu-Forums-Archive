---
title: "upgraded from 13.04 to 13.10 login screen and after a minute x"
date: 2013-10-20
forum: General Help
---

### Post by MikeCyber on 2013-10-20
Hi
after upgrading 13.03 to 13.10 at boot it hangs for around a minute at login (no x) after that it auto logs in/starts normally to x.
What went wrong?
Many thanks

PS: also how to stop services etc. I have around 230 running after: ps -aux
Maybe some keylogger slows it that much....

---

### Post by MikeCyber on 2013-10-20
Hi
after upgrading 13.03 to 13.10 at boot it hangs for around a minute at  login (no x) after that it auto logs in/starts normally to x.
What went wrong?
Many thanks

PS: also how to stop services etc. I have around 230 running after: ps -aux
Maybe some keylogger slows it that much....

---

### Post by drmrgd on 2013-10-20
I don't know what the problem is specifically.  But, I can say that 230 processes is not that unusual.   I just checked, and I have 239 running on my system currently.

---

### Post by philinux on 2013-10-20
Moved to general help. (U+1 is now 14.04 related topics)

Can you post your x session error logs.

---

### Post by MikeCyber on 2013-10-20
you mean dmesg? That's the end:

    4.039109] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=io+mem
[    4.039222] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[    4.039227] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  319.60  Wed Sep 25 14:28:26 PDT 2013
[   11.145315] wlan0: authenticate with 38:60:77:cc:c2:52
[   11.159256] wlan0: send auth to 38:60:77:cc:c2:52 (try 1/3)
[   11.161197] wlan0: authenticated
[   11.165102] wlan0: associate with 38:60:77:cc:c2:52 (try 1/3)
[   11.168601] wlan0: RX AssocResp from 38:60:77:cc:c2:52 (capab=0x431 status=0 aid=1)
[   11.168633] wlan0: associated
[   11.168637] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   65.405272] init: udev-fallback-graphics main process (1747) terminated with status 1
[   65.427568] init: plymouth-splash main process (1774) terminated with status 1
[   65.432843] init: kdm main process (1768) killed by TERM signal
[   65.434591] init: gdm main process (1782) killed by TERM signal
[   66.149003] NVRM: Your system is not currently configured to drive a VGA console
[   66.149006] NVRM: on the primary VGA device. The NVIDIA Linux graphics driver
[   66.149017] NVRM: requires the use of a text-mode VGA console. Use of other console
[   66.149018] NVRM: drivers including, but not limited to, vesafb, may result in
[   66.149019] NVRM: corruption and stability problems, and is not supported.
michael@michael-Ubuntu:~$

what about plymouth/kdm/gdm? As i use autologin maybe they cause that delay?
changed back and forth nvidia drivers without change.
Thanks

PS: looking at ps axu I saw a sleep 60
how silly...tried without success ps aux < ts to copy here.
No idea where that sleep comes from.
How to disable stuff/services. I remember runlevel but that 
has gone.

---

### Post by Toz on 2013-10-20
*Duplicate threads merged.*

---

### Post by Toz on 2013-10-20
> **MikeCyber said:**
> 
PS: looking at ps axu I saw a sleep 60
how silly...tried without success ps aux < ts to copy here.


Try:
```
ps axu > ts
```
...and post back the contents of ts in **[noparse]```
 
```[/noparse]** blocks.

---

### Post by philinux on 2013-10-20
> **MikeCyber said:**
> you mean dmesg? 

No. There's a hidden file in home that shows just X errors .xsession-errors

---

### Post by MikeCyber on 2013-10-20
found and commented that but still the same. 

I give up...so silly to waste time on upgrade which is broken on 90% of all machines.
**We need a rolling release as this is disgusting.**

---

### Post by philinux on 2013-10-20
> **MikeCyber said:**
> found and commented that but still the same. 

I give up...so silly to waste time on upgrade which is broken on 90% of all machines.
**We need a rolling release as this is disgusting.**

I don't see you posting x session errors anywhere.

You've got 10  machines and 9 failed to upgrade properly?

---

### Post by MikeCyber on 2013-10-21
No but tried several years ago with a even worse result.

Wanted to try gnome-shell but it disappeared only classic was available. Hence something went terribly wrong and 
it's way faster to do a clean install.

Never again upgrade for me...

---

### Post by MikeCyber on 2013-10-21
Well it's the same on a clean install. Boot hangs at login for around a minute. Sigh...
The ~.xsession-errors file:
------
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.

---

### Post by philinux on 2013-10-21
> **MikeCyber said:**
> Well it's the same on a clean install. Boot hangs at login for around a minute. Sigh...
The ~.xsession-errors file:
------
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.

Something odd going on. 

1. What are the specs of machine and what make and model graphics card.

2. From the grub menu choose the advance option and select the recovery mode. You'll be able to see the boot process in detail. Note what it's hanging on.

---

### Post by MikeCyber on 2013-10-21
a real downturn...disgusting.
made grub show message and removed whoopie but still the same
removing nvidia etc all the same. it's not always but 90% sigh.
I also cannot install nvidia (unable to build module) only from the repos...might go back 04 soon.

---

### Post by petri.p on 2014-02-08
Was a solution ever found to this?

Today my 13.10 Xubuntu started to do this for me. After boot, it shows the full text screen terminal login: prompt. I can actually login into it. About a minute later, XFCE starts. I have the same errors in dmesg, this is the end of dmesg:

[   22.674850] r8169 0000:03:00.0 eth0: link up
[   22.674856] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   38.915592] usblp 3-10:1.1: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2D12
[   38.915605] usbcore: registered new interface driver usblp
[   38.954784] init: udev-fallback-graphics main process (1146) terminated with status 1
[   39.002299] init: plymouth-splash main process (1164) terminated with status 1
[   39.019998] init: gdm main process (1175) killed by TERM signal

$ cat /etc/X11/default-display-manager
/usr/sbin/lightdm

~$ more .xsession-errors
openConnection: connect: No such file or directory
cannot connect to brltty at :0
Script for cjkv started at run_im.
Script for default started at run_im.

plymouth-splash seems to die..? Once the minute of waiting is over, I get the normal xubuntu graphical login screen, and everything seems to work.

---

