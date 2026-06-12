---
title: "Gparted Live won't boot (Uncompression error)"
date: 2014-05-11
forum: General Help
---

### Post by GameX2 on 2014-05-11
Hi,


I cannot boot on my Gparted Live CD anymore; the BIOS is configured to boot on the CD properly, I get the Welcome Screen, then this appear:

```

Loading /live/vmlinuz...

(15 seconds later)

Loading /live/initrd.img..........

(2 minutes later)

Loading /live/initrd.img.......... ready
Probing EDD (edd=off to disable)..... ok
Decompressing Linux...
uncompression error
--System halted

```

It's weird - I should mention Gparted boot in other computers as it should.  Also, the problem is not my DVD drive, since I can boot other CDs just fine.
I could try and boot from a Gparted ISO from GRUB like I did before, but it's not much easy, messing around with 40_custom, update-grub, I always can't find the right partition to boot on my first attempt, that'll take maybe an hour to get it (Still have trouble with booting from ISO - especially when GRUB is wiped, I have to reconfigure it again).

I don't understand, I booted in Gparted CD just yesterday, and shrinked a few partitions to make more room for Windows 7 (I'm running out of space because of that huge VM that keep growing, and is currently too huge to shrink easilly).  It worked properly, without any errors.  All the OS remain bootables.

But today, I cannot boot Gparted, as I get the error writen above.  What's wrong?  Can it be that a few partitions are nearly full?
I took a screenshot of my partition table from Ubuntu.

[https://dl.dropboxusercontent.com/u/67605655/Capture%20du%202014-05-11%2014%3A54%3A37.png](https://dl.dropboxusercontent.com/u/67605655/Capture%20du%202014-05-11%2014%3A54%3A37.png)

I want to shrink /home, so that I could get the maximum space on Windows 7.  Just for the 2 weeks remaining, so that I could finish the work on that VM, and then I'll delete it, freeing 70GB (!).  But I can't even boot in Gparted Live. :(


What can I do ?

Thanks!

---

### Post by matt_symes on 2014-05-11
Hi

It looks like it's loading the kernel and initramfs files correctly.

Did you hibernate Ubuntu before you shut it down ? These images should be compressed and require uncompressing.

It is also possible you have a problem with the SquashFS root filesystem. That should also be compressed and requires uncompressing.

Have you tried to create a new CD with GParted on it by burning a new image ?

Kind regards

---

### Post by GameX2 on 2014-05-11
> **matt_symes said:**
> Hi

It looks like it's loading the kernel and initramfs files correctly.

Did you hibernate Ubuntu before you shut it down ? These images should be compressed and require uncompressing.

It is also possible you have a problem with the SquashFS root filesystem. That should also be compressed and requires uncompressing.

Have you tried to create a new CD with GParted on it by burning a new image ?

Kind regards

Hi,

Thanks for replying.
I notice loading the kernel and initramfs takes way longer than usual - this takes it takes 2 minutes, while normally it would take 15 seconds.
Althought I can use "Sleep", I cannot hibernate Ubuntu because I have 8GB of RAM and my Swap partition is only 1GB (Small hard disk, and I would never use hibernation even if I could - well not now, not used to it).

I've never heard of SquashFS, I don't know what it is - what I realise is that only a few GB are left in my Ubuntu Root partition, that's all.  I don't know if giving more space would fix the problem.
I did not creating another disk, because it boot fine on another computer (Computer that does not have Linux installed), it's akwards.  But I have a CD-RW, I could try it.

GParted booted 2 days earlier and was fully functional, but now, I can't figure out what happened (Except that I shrinked my partitions, that's pretty much all I did in 2-3 days).

The solution I could try, is boot from the GParted ISO from GRUB, I used to do this before, it's faster than boot from the CD, but it require adding a 40_custom file, and add the correct partition number, I'm not comfortable with that much, for some reason, I can never get it to work on my first attempt.

Thanks

---

### Post by matt_symes on 2014-05-12
Hi

I'm not sure what is the matter with the CD. It may be scratched or in some other way have become damaged.

Have you considered making a bootable USB pen drive instead of a CD ?

> **GameX2 said:**
> 
The solution I could try, is boot from the GParted ISO from GRUB, I used to do this before, it's faster than boot from the CD, but it require adding a 40_custom file, and add the correct partition number, I'm not comfortable with that much, for some reason, I can never get it to work on my first attempt.

Thanks

If you are interested in booing GParted from the hard drive, here is my 40_custom entry to boot GParted. 

I'm using the x86 version and not the x86_64 version even though this notebook has a 64-bit chip in it. It should work for a 64 bit ISO as well though.

```
menuentry "GParted" {
        [B]set isofile="[COLOR=#008000]/my_isos/gparted-live-0.16.1-1-i486.iso[/COLOR]"
        loopback loop [COLOR=#ff0000](hd0,11)[/COLOR]$isofile[/B]
        linux (loop)/live/vmlinuz findiso=$isofile boot=live config toram=filesystem.squashfs  noswap noprompt  ip=frommedia  nosplash i915.blacklist=yes radeonhd.blacklist=yes nouveau.blacklist=yes vmwgfx.blacklist=yes
        initrd (loop)/live/initrd.img
}
```

You would have to change the two lines i have highlighted in bold to point to the correct location for the ISO file on your hard drive but, apart from that, it should work for you.

You can find the drive/partition combination (highlighted in red above) using 

```
sudo parted -l
```

or from

```
sudo blkid
```

From that partition, you will need to add the full path (highlighted in green above).

I hope this helps you.

Kind regards

---

### Post by GameX2 on 2014-05-12
> **matt_symes said:**
> Hi

I'm not sure what is the matter with the CD. It may be scratched or in some other way have become damaged.

Have you considered making a bootable USB pen drive instead of a CD ?



If you are interested in booing GParted from the hard drive, here is my 40_custom entry to boot GParted.

I'm using the x86 version and not the x86_64 version even though this notebook has a 64-bit chip in it. It should work for a 64 bit ISO as well though.

```
menuentry "GParted" {
        [B]set isofile="[COLOR=#008000]/my_isos/gparted-live-0.16.1-1-i486.iso[/COLOR]"
        loopback loop [COLOR=#ff0000](hd0,11)[/COLOR]$isofile[/B]
        linux (loop)/live/vmlinuz findiso=$isofile boot=live config toram=filesystem.squashfs  noswap noprompt  ip=frommedia  nosplash i915.blacklist=yes radeonhd.blacklist=yes nouveau.blacklist=yes vmwgfx.blacklist=yes
        initrd (loop)/live/initrd.img
}
```

You would have to change the two lines i have highlighted in bold to point to the correct location for the ISO file on your hard drive but, apart from that, it should work for you.

You can find the drive/partition combination (highlighted in red above) using 

```
sudo parted -l
```

or from

```
sudo blkid
```

From that partition, you will need to add the full path (highlighted in green above).

I hope this helps you.

Kind regards

Hi,


That was really helpful, thank you.  I changed my 40_custom file exactly like yours (May I ask what radeonhd.blacklist=yesdoes?  I have an integrated Intel HD 3000 card, and not a Radeon).  Updated GRUB and now GParted appear in the GRUB menu as it should.  When I booted, I did saw "Decompressing Linux" really fast, and it seemed like Gparted was booting, but 5 seconds later, I got a Kernel Panic. :O

This is what's visible on the screen:

```

/init : line 331: can't create /dev/null: Too many levels of symbolic links
**Something went badly wrong in the initramfs**
/init: line 333: 6: Bad file descriptor
[  4.828806] Kernel panic - not syncing: Attempted to kill init! exitcode=0x00000200
[  4.828915] CPU: 2 PID: 1 Comm: init Tainted: G     C   3.13-1-amd64 #1 Debian 3.13.7-1
[  4.829004] Hardware name: LENOVO 1141BTF/1141BTF, BIOS 8HET44WW(1.26) 08/07/2013

*[Random rumbers]*

[  4.829870] Call Trace:

*[More random rumbers]*

Last line:
[  4.830362] [<fffffff814ae4f9>] ? system_call_fastpath+0x16/0x1b
_


```

Wow, it's akwards.  I especially wonder what's that line supposed to mean at all: Something went badly wrong in the initramfs.
It did booted 3 days ago... :/ I did not changed anything major since, especially in Ubuntu, was using Windows 7 mostly.  The only difference is that the Root partition is now smaller.

Maybe it's my Root partition, the problem.  Only 800MB or so is left.  I may try to boot from a USB Drive, now.

---

### Post by matt_symes on 2014-05-12
Hi

> /init : line 331: can't create /dev/null: Too many levels of symbolic links 
**Something went badly wrong in the initramfs** 
/init: line 333: 6: Bad file descriptor

That's pretty serious. Try downloading the GParted ISO again from their website.

The iso should be loaded into ram so i would be surprised if the space on your root partition was the problem.

How much ram do you have ?

> radeonhd.blacklist=yes

That should blacklist the radeon driver.

Kind regards

---

### Post by GameX2 on 2014-05-12
> **matt_symes said:**
> Hi



That's pretty serious. Try downloading the GParted ISO again from their website.

The iso should be loaded into ram so i would be surprised if the space on your root partition was the problem.

How much ram do you have ?



That should blacklist the radeon driver.

Kind regards

I will download a x86 ISO, and try to boot it from USB.
I have 8GB of RAM (2x4GB DDR3), I may try a Memtest86, although I don't have any apparent problem on Ubuntu or Windows 7 now.

Still don't get why it worked 3 days earlier.  Anyways, I will try to boot from a USB drive, and run a Memtest86.  Will let you know about it.

Thanks

---

### Post by GameX2 on 2014-05-13
Allright, I downloaded a x86 ZIP file that I downloaded from the GParted website; extracted it on my USB drive and ran the Windows batch file to make it bootable -And it did booted succesfully!  Actually, now typing this from the GParted browser, just before I start partitioning before the night.I m still concerned however - how could we explain that the CD, nor the GRUB entry are bootable?  I ran Memtest86+, and it did not found any error.For GRUB, maybe that the x64 ISO simply wont work, or has a different config than the x86 ISO, but I still dont understand why the CD wont boot, while the problem is not the CD, or the DVD drive, they all work.  I m wondering, because I use this CD really often (Or booting from GRUB if I have access, its a lot faster.  USB is also a lot faster than CD obviously).  Maybe thats a hint that something is wrong with my Ubuntu partition.. (Fresh/New install of Ubuntu 14.04, with a old 13.04 /home partition.. Currently some stuff freak out a little in Ubuntu, because of that /home that need clean-up, but thats all, the Ubuntu install is brand-new).Thank you for you advices, at least I can start partitionning. =)

---

### Post by matt_symes on 2014-05-14
Hi

Personally, i suspect the CD Rom or the iso file may have become damaged in some way.

I would be very surprised if the problem was due to hard drive space on your root partition however i would never completely discount it until i had eliminated it as the actual cause.

Anyway, you have a bootable USB pen drive and that is good enough for me :D

Kind regards

---

