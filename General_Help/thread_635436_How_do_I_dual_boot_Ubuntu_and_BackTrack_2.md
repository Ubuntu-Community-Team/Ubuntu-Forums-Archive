---
title: "How do I dual boot Ubuntu and Back|Track 2?"
date: 2007-12-08
forum: General Help
---

### Post by paranoiahax on 2007-12-08
Hi, I've recently got fed up with Windows so wiped my Windows partition completely, and decided to try out another Distribution of Linux, and my friend recommended Back|Track2, a Slackware distribution for security penetration and testing.

Now I downloaded the live CD, booted it up and installed it successfully, I can even access it from Ubuntu, see it all there nicely.

However, I am unsure on how to access it. I currently have GRUB as my boot loader, would be prepared to switch to LiLo if I had to but I like GRUB the way it is as I've customized it all nicely and I'm quite familiar with it.

As far as I'm aware, Back|Track2 is installed on (hd0,1) and my Ubuntu is installed on (hd0,0)

I have tried doing what I did whenever Windoze screwed up GRUB by "root (hd0,0)" and "(setup (hd0)" and other variations of this but it does not seem to have worked. 

Here is a snippet of my current menu.lst:

```
title		Ubuntu
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
password	--md5 *MY MD5 HASH*

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root
```

I have tried playing about with this also, e.g. by adding a selection for Back|Track2 like so:

```
title		Back|Track 2
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro quiet splash
initrd		/boot/initrd.img-2.5.22-14-generic
password	--md5 *MY MD5 HASH*
```

but this didn't work and I realised that it probably wouldn't work because it's not the right kernel, but I just tried editing the root partition.

So I was wondering if anyone could give me any help, on how to detect and set up the GRUB automatically, or even manually in menu.lst

P.S. I've tried "sudo update-grub" too, but this did not recognize my other partition and just annoyed me because it added loads of unwanted selections and got rid of my passwords.

Thanks in advance, Para

---

### Post by confused57 on 2007-12-09
You can probably use symlinking to boot your other Linux OS:
[http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink](http://users.bigpond.net.au/hermanzone/p15.htm#3._Symlink)

I'm currently booting Slackware12.0, using this method...if you want to edit your menu.lst manually:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
add your BackTrack boot entry to the very end of your menu.lst file, quit & save.

Here's my Slackware entry(one of them):
```
title    Slackware 12.0
root   (hd1,5)
kernel /boot/vmlinuz root=/dev/sda6 ro quiet splash
initrd /initrd.img
boot
```
this entry boots the "vmlinuz-huge-smp-2.6.21.5-smp, which I determined by entering "uname -a" in a terminal.

Using the methods in the link I gave you above, you can determine the current kernel(s) listed either in your root and/or /boot directores & adjust your boot entry accordingly.  I probably don't need them, but I also added separate boot entries for the various kernels contained in Slackware 12.0, i.e.
vmlinuz-generic-2.6.21.5
vmlinuz-huge-2.6.21.5
vmlinuz-huge-smp-2.6.21.5-smp

Your entry would probably be something like:
```
title   BackTrack
root  (hd0,1)
kernel  /boot/vmlinuz root=/dev/sda2 ro quiet splash
initrd  /initrd.img
boot
```
you would need to determine if Backtrack has an initrd or not(see the thread above)...if your HD is IDE, you may need to use /dev/hda2.

---

### Post by paranoiahax on 2007-12-09
Right, I've been experimenting a bit with this and still no luck.

I added loads of lines so save me from trying loads of different ones and to keep rebooting lol.

```

title    Back|Track 1
root	(hd0,1)
kernel	/boot/vmlinuz root=/dev/sda ro quiet splash
initrd	/initrd.img

title   BackTrack 2
root	(hd0,1)
kernel  /boot/vmlinuz root=/dev/sda2 ro quiet splash
initrd  /initrd.img
boot

title    BackTrack 3
root	(hd0,1)
kernel	/boot/vmlinuz root=/dev/sda ro quiet splash
initrd	/initrd.img
boot

title   BackTrack 4
root	(hd0,1)
kernel  /boot/vmlinuz root=/dev/sda2 ro quiet splash
initrd  /initrd.img

```

is what I tried. 

I also tried:

```

saxon@saxon-laptop:~$ sudo fdisk -lu
[sudo] password for saxon:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x83bc8e42

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    74188169    37094053+  83  Linux
/dev/sda2   *    74188170   153292229    39552030    7  HPFS/NTFS
/dev/sda3       153292230   156296384     1502077+   5  Extended
/dev/sda5       153292293   156296384     1502046   82  Linux swap / Solaris

```

to test what my hard drive partition table looked like. I'm not actually all too sure which one is which funnily enough.

I have also checked my Back Track directories, and cannot find any trace of an initrd or vmlinuz so i think this could be half of the problem.

Have you got any other suggestions?

Btw, the error message I keep getting when highlighting a selection and trying to boot it is:

"Error 17: Cannot mount selected partition"

Thanks in advance, Para

---

### Post by confused57 on 2007-12-09
You might try reinstalling BackTrack & making sure to format sda2 as ext3 or reiserfs.

Before you do this, you could explore your computer using grub's CLI:
[http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI](http://users.bigpond.net.au/hermanzone/p15.htm#How_To_Boot_Linux_from_GRUBs_CLI)

This may tell you a little more about the filesystem & if it is capable of being booted...I don't think so, since "fdisk -lu" is showing it as NTFS?  You're able to boot into Ubuntu OK?

---

### Post by paranoiahax on 2007-12-09
yeah, Ubuntu works fine. And I had Windows on that partition, but I could swear I formatted it to ext3 before installing Back Track lol. Well, I'm gonna format it again, wish me luck :P I'll let you know how I got on and I'll take a look at that link too. Thanks!

---

