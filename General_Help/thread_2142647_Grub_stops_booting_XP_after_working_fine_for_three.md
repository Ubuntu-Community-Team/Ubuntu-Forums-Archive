---
title: "Grub stops booting XP after working fine for three + years!"
date: 2013-05-06
forum: General Help
---

### Post by mister_p_1998 on 2013-05-06
Ok Guys,
Im running Ubuntu Hardy 8.04 (old but does all I need)

Booted up yesterday tried to get to boot XP from Grub and got 'Error 13 invalid or unsupported executeable format' error
Spec is 
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x31853184

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24136   193872388+  83  Linux
/dev/sda2           24137       24321     1486012+   5  Extended
/dev/sda3           24322       48641   195350400   83  Linux
/dev/sda4           48642      121601   586051200   83  Linux
/dev/sda5           24137       24321     1485981   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00093e4e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1      127482  1023999133+  83  Linux
/dev/sdb2          127483      182401   441136867+   5  Extended
/dev/sdb5          127483      182401   441134080   83  Linux

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcad7cad7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       19456   156280288+   7  HPFS/NTFS

SDC1 is the XP disk,

Heres my Grub

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.


## ## End Default Options ##

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-29-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-29-generic root=UUID=766d9604-e98f-4075-9f8d-b12868cd1053 ro quiet splash
initrd		/boot/initrd.img-2.6.24-29-generic
quiet

title		Ubuntu 8.04.4 LTS, kernel 2.6.24-29-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-29-generic root=UUID=766d9604-e98f-4075-9f8d-b12868cd1053 ro single
initrd		/boot/initrd.img-2.6.24-29-generic



title		Ubuntu 8.04.4 LTS, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

#

### END DEBIAN AUTOMAGIC KERNELS LIST

		# Windows XP
title Microsoft Windows XP Professional
root (hd2,0) 
map (hd2) (hd0)
map (hd0) (hd2)
makeactive
chainloader +1
#

Absolutely NOTHING has been changed, If I unplug all but the XP drive, it boots fine, just not from grub. Ive pored over the grub setting and all looks fine to me, 
Any ideas uys?
Steve

---

### Post by oldfred on 2013-05-06
Have not used grub legacy for ages. Had to dig deep in my old notes to find Herman's page on errors.

[http://members.iinet.net.au/~herman546/p15.html#13](http://members.iinet.net.au/~herman546/p15.html#13)

It may be that you need to run chkdsk on your NTFS partition? You have to do that from your XP install disk as no Linux repair CDs have a way to run it. I have used a Windows 7 repairCD to run chkdsk on my XP and it worked better than the XP chkdsk. But it converted PBR - partition boot sector to Window 7 type (boot with bootmgr) and I had to change it back to XP type (boot with ntldr). 
I have had issues from Linux on NTFS partitions even when XP still booted. But chkdsk resolved problems and XP booted a bit faster (still slow).

---

### Post by mister_p_1998 on 2013-05-07
Sorted it!
Duh! I pulled the battery out and blanked the cmos, it changed the disk priority making the XP drive essentially hd1 instead of hd2 which grub was looking for. Changed the XP drive back to third drive in the BIOS and it all worked again!

Steve

---

### Post by mörgæs on 2013-05-07
Although is works you should install a newer version. 8.04 is out of support and does not receive security bug fixes.

---

### Post by col48 on 2013-05-07
Hi Mister P

Worth thinking over what morgaes says.  If you will *never* need to change and are happy to take the small(?) security risk, fair enough.  But if you are forced to change (whether because something breaks and you have lost the Live CD, or can't obtain a driver for a replacement piece of kit) you will be doing so under pressure - and perhaps with deadlines looming which need a fully functioning computer+printer+email+etc.  If you switch now (ish) you can do so at a time of your own choosing and take your time to get the new version fully operational.  It is also the case that Hardy expertise is Harder to find (just as Lucid expertise will begin to be less Lucid, Precise is Precisely at its peak and Raring is Raring to go -- sorry, I couldn't resist that distraction!) as time goes on and old memories of how to fix it may become unreliable.  Not everyone is as organised as oldfred, unfortunately.

My own suggestion is to set up dual booting between Hardy and Precise (or the next LTS version in due course). You can then set up Precise while you still have a working Hardy.  I did this (Hardy/Lucid) a couple of years ago with a lot of help from oldfred and kansasnoob and it meant I could switch smoothly.  I'll add the link to the thread in a minute.

Here is the link:
[http://ubuntuforums.org/showthread.php?t=1687962]("http://ubuntuforums.org/showthread.php?t=1687962")

---

### Post by mister_p_1998 on 2013-05-07
Hmm been thinking about it for a while but hate the new Gnome, run Lucid at work, but thats out of date now isnt it?
Probably gonna go mate or Cinnamon at some point, but even they are not completely like the old gnome, I've got several pc's so not a huge problem if one goes down.

Steve

---

### Post by oldfred on 2013-05-07
I stayed with 10.10 for quite a while before upgrading to 12.04. But I installed gnome-panel or what was gnome-fallback in earlier versions. That is almost like the old gnome2 with some changes or like an update. I have a 4:3 monitor so the Unity interface does not work as well as top & bottom panels for me. Unity has improved, but I still have issues on separating already launched apps and wanting another new app to launch.

       gnome3 classic
sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 
[http://ubuntuforums.org/showthread.php?t=2090021](http://ubuntuforums.org/showthread.php?t=2090021)
[http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed](http://www.omgubuntu.co.uk/2012/03/gnome-classic-in-ubuntu-12-04-its-like-nothing-ever-changed)

---

