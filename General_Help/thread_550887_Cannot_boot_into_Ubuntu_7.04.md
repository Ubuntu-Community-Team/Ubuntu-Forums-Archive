---
title: "Cannot boot into Ubuntu 7.04"
date: 2007-09-14
forum: General Help
---

### Post by dontom on 2007-09-14
Well, it's not exactly true, maybe in 1 of 10 reboots I can get in. But today it doesn't seem like that either.
When I try to boot the regular way, it stops at the loading screen with Ubuntu logo and the progress bar. If I press ctrl + alt + f1, I can see the text 'Loading, please wait...' as well as 'Kernel alive', 'kernel direct mapping tables up to 100000000 @ 8000-d000' at the bottom of the screen.

Then after a while, this shows up;
'Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Alert! /dev/disk/by-uuid/0ec1266c-830f-4b6a-9198-a409bfb5a31f does not exist.
Dropping to a shell!

And when I try to boot recovery mode it usually stops at ;

[ 23.410230] hda: ATAP 24X DVD-ROM DVD-R-RAM .., UDMA(33)
[ 23.410693] Uniform CD-ROM driver Revision: 3.20

But at this particular boot I got a bit further;

[ 23.650069] usb 4-2: new high speed USB device using ehci_hcd and adress 2
[ 23.790832] usb 4-2: configuration #1 chosen from 1 choice
[ 23.913109] eth0: forcedeth.c: subsystem: 01025:0127 bound to 0000:00:0a.0
Done.

Then I get the same error as when regular boot;

'Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
Alert! /dev/disk/by-uuid/0ec1266c-830f-4b6a-9198-a409bfb5a31f does not exist.
Dropping to a shell!

I'm using kernel 2.6.20-16.

Thanks in advance,
Tom.

---

### Post by dontom on 2007-09-14
*bump*

---

### Post by jamvegan on 2007-09-14
I'm not certain that this is the problem (but trying this won't hurt, it just may not work)...

If you know the drive and partition of your Ubuntu / (or /boot, if you gave it its own partition), then try this: 

1) When you see the grub boot menu, highlight the Ubuntu entry and type "e" (for edit).

2) Change the kernel line so that instead of looking something like this:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=b497a47a-fd39-41e1-8774-ab4dd239d2f1 ro quiet splash
```
it looks something like this:
```
kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/hda2 ro quiet splash
```
where "/dev/hda2" is replaced with the correct partition for your system.  Actually, you can get that from the root line of the entry, if you don't already know it.  The root line will look something like:
```
root            (hd0,1)
```
The part before the comma is the drive, starting with "0" instead of "a", so hd0=/dev/hda (or /dev/sda, depending on the type of drive), and the number after the comma is the partition, starting from 0 rather than 1, so hd0,1=/dev/hda2 (or /dev/sda2).

3) When you're done editing the entry, type "b" to boot.

If it boots correctly, then you can make the change permanent by editing /boot/grub/menu.lst with the same change.

Hope this helps!

---

### Post by dontom on 2007-09-14
Thanks for your tip.
The first entry looks like;
'root  (hd0,2)'

So I figured I'll put; kernel          /boot/vmlinuz-2.6.20-16-generic root=/dev/hda3 ro quiet splash
into the line.
That didn't work, I also tried with root=/dev/hda2, that didn't work either.
But thanks alot for the response :)

---

### Post by confused57 on 2007-09-14
The UUID in question may have changed, you can mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

This guide explains how to check the current UUID's on your system:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

Basically, what you would do is run:
```
blkid
```

Use the first link above to mount your root partition,then compare the output of "blkid" with the UUID's in your /etc/fstab and /boot/grub/menu.lst.  If they are incorrect, you could just copy & paste the correct UUID.

---

### Post by dontom on 2007-09-14
Thanks again for a great tip.
So I ran blkid, and found the UUID of my EXT3 partition, which contains linux, and it is exactly the same as the one in Grub. So no luck there either :S

The weird thing is that it works some times, in about every 10 reboots or something.
So it seems there is something else interrupting the boot.

---

### Post by jamvegan on 2007-09-15
Is the UUID of your Linux partition the one that shows up in the error message ("Alert! /dev/disk/by-uuid/0ec1266c-830f-4b6a-9198-a409bfb5a31f does not exist.)"?

---

### Post by dontom on 2007-09-15
> **jamvegan said:**
> Is the UUID of your Linux partition the one that shows up in the error message ("Alert! /dev/disk/by-uuid/0ec1266c-830f-4b6a-9198-a409bfb5a31f does not exist.)"?

Yes, exactly the same.

---

### Post by baked on 2007-10-14
Hello, has there been any resolution to this?  I am having the same problem and I am for sure the UUID is the same as what is supposed to boot (it is my main partition which is '/').It boots sometimes, but not always.  I can not figure out any pattern to this, so I guess I am going to have to change GRUB to load off the drive name instead of all this UUID stuff.

I would like to report this as a bug if it is not already.  Any help in trying to find out why this is happening would really be appreciated.  I have a hp2610us laptop, which has a nvidia mother board and chipset.

---

### Post by mrfilgueira on 2008-03-26
I do have the same issue with Ubuntu 7.10. I had a working install and changed the whole hardware. I started live with Ubuntu 7.10 x86, installed, and when restarting I got the same error. I think there is a module missing for the chipset? The mainboard is an ASUS M2N-DVI. It uses Nvidia 630a/7050.

---

