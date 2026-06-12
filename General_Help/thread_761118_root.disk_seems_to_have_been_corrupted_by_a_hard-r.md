---
title: "root.disk seems to have been corrupted by a hard-reset of Ubuntu"
date: 2008-04-20
forum: General Help
---

### Post by inzania on 2008-04-20
It seems to have started when Ubuntu 8.04 froze - I restarted manually, and was dropped to the (initramfs) prompt from BusyBox.  Restarting again in verbose mode revealed that "/host/ubuntu/disks/root.disk does not exist."  When I navigate to the folder and do a "ls" from the command prompt, it gives me an I/O error on attempting to read the file.  I booted into windows and found the file in file explorer.  I did a chkdsk /fix on Drive C (NTFS by the way), and though the chkdsk stated that it fixed problems specifically within the root.disk file, attempting to boot into ubuntu still yields the same problem.

Oh, I've also tried booting to the older (x.12 instead of x.15) kernel.  Same error.

I'm out of ideas - how can I fix my root.disk without completely re-installing ubuntu?

Thanks.

---

### Post by ago on 2008-04-21
If checkdsk /r does not do it you can try with other partitioning tools, otherwise you can try to mount off a live CD to recover the files. It might be necessary to use the -f mount option to force the mount.

For the next time see: [https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a](https://wiki.ubuntu.com/WubiGuide#head-3daaf6dbfcade2cd0a9b85b8ca00590ecb91426a)

---

### Post by inzania on 2008-04-22
Thanks for the link, I was unaware of the SYSREQ hotkeys, and was working with Cntrl+Alt+Del and Cntrl+Alt+Backspace.

I'm in the unfortunate situation of being unable to create a CD any time soon (long story).  I know it's a long shot but... is there any other way to create a root.disk file that will at least let me boot?  I can always replace the files.

---

### Post by ago on 2008-04-22
> **inzania said:**
> Thanks for the link, I was unaware of the SYSREQ hotkeys, and was working with Cntrl+Alt+Del and Cntrl+Alt+Backspace.

I'm in the unfortunate situation of being unable to create a CD any time soon (long story).  I know it's a long shot but... is there any other way to create a root.disk file that will at least let me boot?  I can always replace the files.

Add the following at the end of c:\ubuntu\disks\boot\grub\menu.lst

```
title Demo mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel boot=casper iso-scan/filename=/ubuntu/install/XXX
initrd /ubuntu/install/boot/initrd.gz
boot

```
Replace XXX with the name of the ISO in /ubuntu/install
Then press esc at boot and select Demo Mode. That is equivalent to boot off Live CD

---

### Post by fitzydog on 2008-08-08
ok, so if it boots into Live CD mode, how do we get it into regular mode? Or is there a way?

---

### Post by Atrevidoweb on 2008-08-15
> **ago said:**
> Add the following at the end of c:\ubuntu\disks\boot\grub\menu.lst

```
title Demo mode
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel boot=casper iso-scan/filename=/ubuntu/install/XXX
initrd /ubuntu/install/boot/initrd.gz
boot

```
Replace XXX with the name of the ISO in /ubuntu/install
Then press esc at boot and select Demo Mode. That is equivalent to boot off Live CD

Hi, and thanks.
I'm having a similar problem, with Ubuntu 8.04 installed on wxp.
I tried your sugestion to enter in demo mode but it's giving me this error message:

```
(hd0,0)
Filesystem type is ntfs, partition type 0x7
kernel boot=casper iso-scan/filename=/ubuntu/install/installation.iso

Error 1: Filename must be either an absolute pathname or blocklist

```

I'm really new to ubuntu so, no idea how to correct this.
The ubuntu directory is on c:\ubuntu\... 

Thanks in advance
Atrevidoweb

---

### Post by indiessance on 2008-12-26
think I ran into the same exact problem, perhaps caused by a hard reset while running memtest.

---

### Post by shinglei on 2009-06-09
Hello all,

I'm having the same problem as inzania. Currently I'm willing to go with two options:
(1) find some way to boot ubuntu successfully (which probably involves fixing the corrupt root.disk, I'm guessing)
(2) find some way to access the files I had on ubuntu so that I can just reinstall it
The problem with (1) is that I couldn't find the ISO in ubuntu/install that ago was referring to, and haven't been able to find a solution anywhere else online.
The problem with (2) is that I'm using Wubi, which seems to make things more difficult. I tried using explore2fs, but I don't think I have an ext2 or ext3 partition (because of Wubi)

Lastly, I'm new to Linux. That's mainly why I used Wubi rather than partition my drive- I just wanted to see what ubuntu was like first. It's great, but I manually rebooted it and now I can't seem to get it to work.

So um, would anyone care to enlighten me?
Thanks =)

---

