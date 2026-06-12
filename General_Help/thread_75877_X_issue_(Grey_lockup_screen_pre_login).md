---
title: "X issue (Grey lockup screen pre login)"
date: 2005-10-14
forum: General Help
---

### Post by Maelstrm on 2005-10-14
Ok ladies and (more likely) gents, I'm having a seriously annoying recurring problem here:

First off, I'll just let you know I'm pretty new to linux (2-3 weeks experience), but I'm getting a reasonable grip on the basics. I've got two boxes I'm trying to set up to both dual boot Windows and Kubuntu.

The older box (Darth) now works 100% fine.

Following the exact same install method my faster, newer, snazzier pc (Mael) dies. Loading KDM locks at the grey pre-login screen, with a normal mouse cursor that can be moved.

Hardware:
Athlon XP 2800+
Nvidia Nforce2 based motherboard (MSI K7N2 Delta-L) - onboard sound/lan
Nvidia Geforce 6800NU video card
Hercules Fortissemo II sound card
WD 200GB harddrive

To date I've done:

1) Install windows
2) Update windows to SP2 + put on drivers
3) Install Kubuntu 5.04
4) Find KDM doesn't start, reboot to recovery mode, apt-get dist-update
5) try kdm (grey lockup)
6) reboot to recovery mode, startx (grey lockup)

Repeat steps 1-4, same issue.

Repeat steps 1-3 but with Kubuntu 5.10, and I've just gotten another grey lockup.

When locked up, ctrl-alt-del and ctr-alt-f(key) don't do jack, regardless of whether I've booted via standard bootup or started kdm manually through recovery mode.

In the mean time the Windows install is running fine, and all of the hardware is just dandy.

Partitions look like this [20gb Windows] [10gb \] [500mb swap] [160gb fat32 shared storage]

I've zipped my /var/logs up and thrown them here:
[http://www.maelstrm.fuckyouanddie.com/SA/log.zip](http://www.maelstrm.fuckyouanddie.com/SA/log.zip)

Bits that are probably relevant:
[quote=daemon.log.0]
Oct 14 19:13:19 localhost modprobe: FATAL: Error inserting apm (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/apm.ko): No such device 
Oct 14 19:13:50 localhost hcid[20243]: Bluetooth HCI daemon
Oct 14 19:13:50 localhost sdpd[20249]: Bluetooth SDP daemon 
Oct 14 19:18:13 localhost modprobe: FATAL: Error inserting apm (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/apm.ko): No such device 
Oct 14 19:18:35 localhost modprobe: FATAL: Error inserting apm (/lib/modules/2.6.12-9-386/kernel/arch/i386/kernel/apm.ko): No such device 
Oct 14 19:18:36 localhost init: Re-reading inittab
Oct 14 19:18:38 localhost kdm_greet[25095]: Can't open default user face
[/quote]

[quote=kdm.log]
==) Using config file: "/etc/X11/xorg.conf"
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o":  No symbols found
Skipping "/usr/X11R6/lib/modules/libfb.a:fbmmx.o":  No symbols found
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
QImage::convertDepth: Image is a null image
QImage::smoothScale: Image is a null image
[/quote]


Help... please :(

---

### Post by adwait on 2005-10-14
Do you have the correct graphic drivers? Try running 
```
sudo dpkg-reconfigure xserver-xorg
```
(That must be like the nth time I suggested in 2 days alone........people must be beginning to think that's all I know :p)

---

### Post by Maelstrm on 2005-10-14
Thanks for responding!

I saw that in another similar thread. Ran through it and picked all the default options.

Anything in particular you think I should change?

Since I've done a couple of complete reinstalls so it seems to be a problem with a default somewhere rather than a config change that I've done to break it. I don't know enough about what does what to fix that sort of thing though.

Also I've tried to download the latest build of the linux drivers for my video card (which is reasonably new -- 9 months). I've got all the required packages, but it wants my kernel source since apparently nVidia don't have anything related to it on their FTP.

Where can I get the kernel source for Kubuntu 5.10? The latest linux source package I could see in the official Ubuntu repositories seemed a releases behind.

Do you think it would be a video card issue or X configuration error? I was really taking a stab when I picked this title, because I don't properly understand how everything interacts.

Again, thanks for any and all help :)

---

### Post by adwait on 2005-10-14
Most probably an issue with your card, because I see lots of problems with drivers and NVidia cards. Search the forums, you'll find quite a few posts about NVIDIA hardware....There's gotta be something there that will work for you.

---

### Post by Maelstrm on 2005-10-16
Finally fixed. If you have the same issue, try installing the nvidia drivers (you'll have to wget them from their website and grab a few packes to get it to run).

Thanks adwait

---

### Post by mr_teal on 2005-12-09
I have the same problem, but my video card is an Ati Radeon X550... Maybe the NVidia drivers fix something about the motherboard (mine is based on NVidia chipset...)?
I don't think the problem is related to the video card because  X server seems to start properly. On the other hand, I have experienced the same behaviour with Kubuntu 5.10 and Ubuntu 5.10 (which is not based on KDE) so the problem cannot be kdm... 
I try to install NVidia stuff now, I'll let you know...

---

### Post by abrls on 2005-12-11
Maelstrm,

I have similar problem also.
Can you provide the step-by-step instruction for installing the Nvidia binary driver from the recovery mode, please?

BTW, do you know how to setup PPPoE in text-mode (no GUI)?

---

