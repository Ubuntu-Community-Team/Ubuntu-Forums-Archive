---
title: "Boot problems with 1.6.15-27-386"
date: 2006-11-09
forum: General Help
---

### Post by ernster on 2006-11-09
This morning, I booted my laptop up and ran into a problem. This is not a new install (been running fine for about 6 mths), and I have kubuntu on top. Yesterday, I applied some updates (2 were available) and then shut down the system. Something has changed.

While loading the kernel, it tries to mount root and fails, then drops into ash for me to make changes if necessary.

The messages I get are:

mount: Mounting /dev/hda2 on /root failed: No such device
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mountin /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

Then it drops to BusyBox v1.01, with one last error message that says "/bin/sh: can't access tty; job control turned off

Then prompt.

I went into Grub's boot commands and found these commands:

"root (hd0,1)
 kernel /boot/vmlinuz-2.6.15-27-386 root =/dev/hda2.ro quiet no splash
 initrd /boot/initrd.img-2.6.15-27-386
 savedefault
 boot"


BTW: When I cd to /dev, there is an entry for hda2.

Any thoughts on this?

A bit about me: I am not exactly a Unix n00b, but I am definately a n00b when it comes to the guts of Linux, and it's been so long since I've had to do anything at this level, I'll need some hand-holding.

---

### Post by ernster on 2006-11-14
Okay, so 5 days and no response? Does anyone have any idea on this issue?

---

### Post by zgornel on 2006-11-14
What were the updates ? Is there a "." between hda2 and ro in the grub kernel line ?

---

### Post by rjpiercy2 on 2006-11-21
Hi ernster,

If it is any consolation, I haven't been able to boot into a kernel since 2.6.15-25.  My old kernels still show up in the grub menu (the timeout was only 3 secs, so you have to watch for that and hit ESC).  Maybe that will be an option for you.  

2.6.15-26, 2.6.15-27 hang on the boot when it tries to mount the root file system.  The last thing it tries is:

IP-Config eth0 hwaddress 00:30:1b:28:30:36 mtu 1500 DHCP RARP

My ethernet controller is VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74).

I have been scouring the net for a solution.  I think I may try to build my own kernel and see if that works.  If anyone has any ideas, I am all ears.    

My cpu is Intel(R) Pentium(R) 4 CPU 2.66GHz with 512M Ram

lspci gives:

0000:00:00.0 Host bridge: VIA Technologies, Inc. VT8374 P4X400 Host Controller/AGP Bridge (rev 03)
0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
0000:00:09.0 Communication controller: Agere Systems V.92 56K WinModem (rev 02)
0000:00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
0000:00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
0000:00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
0000:00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
0000:00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)
0000:01:00.1 Display controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (Secondary) (rev 01)

I hope you find a solution.  If I do, I will post here.

---

