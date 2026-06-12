---
title: "[SOLVED] Tricky partition boot"
date: 2007-10-26
forum: General Help
---

### Post by GZBurtchell on 2007-10-26
I'm trying to boot from a partition I created, basically what I'm trying to do is trick Ubuntu Studio to install from this partition instead of a dvd drive, as from the instructions found at the help.ubuntu.com/community/Installation/FromLinux page. Everything else went ok, but I'm having a problem getting it to boot. I got this error message: Error 19: Kernal must be loaded before initrd. 

Here's the entry I put in the menu.lst file for Grub (according to the instructions)

title           Installer

root           (hd1,1)

kernal        /casper/vmlinuz boot=casper root=/dev/ram ramdisk_size=1048576 rw

initrd          /casper/initrd.gz


The instructions for doing this are for Ubuntu 7.04/Ubuntu Studio 7.04, and I'm doing this with the 7.10 versions of both. If there's a difference  and  something needs to be changed on the Kernal & Initrd lines, I'm at a loss there. I'm amazed I got this far with something like this and I'm learning as I go. Can anyone help?

---

### Post by GZBurtchell on 2007-10-26
Anyone? I extracted the Ubuntu Studio 7.10 iso to a partition on my hard drive but I don't know how to set up Grub to boot from it. I've tried several things but I keep getting: Error 19: kernel must be loaded before initrd. Can anyone help?

---

### Post by meierfra on 2007-10-26
I don't know whether it will fix your problem, but you misspelled kernel. It's supposed to be "kernel" not "kernal"

---

### Post by GZBurtchell on 2007-10-26
> **meierfra said:**
> I don't know whether it will fix your problem, but you misspelled kernel. It's supposed to be "kernel" not "kernal"

You have got to be kidding. There, fixed it. Still can't boot from the partition.

---

### Post by meierfra on 2007-10-26
Still the same error message?

---

### Post by GZBurtchell on 2007-10-27
> **meierfra said:**
> Still the same error message?


Sorry, a little frustrated with this. What I'm getting now is Error 17: Cannot Mount Selected Partition. I'm guessing I have to add some sort of mount command in the menu.lst entry before the kernel & initrd lines.

---

### Post by meierfra on 2007-10-27
I would guess that  "(hd1,1)"  is wrong.  (hd1,1) refers to the second partition on the second hard drive. Could you post the output of 

```
sudo fdisk  -l     (l is a lower case L)
```

---

### Post by GZBurtchell on 2007-10-27
> **meierfra said:**
> I would guess that  "(hd1,1)"  is wrong.  (hd1,1) refers to the second partition on the second hard drive. Could you post the output of 

```
sudo fdisk  -l     (l is a lower case L)
```



I can tell you what the partitions are without the fdisk -l. I've seen them enough times already.:-) In drive/partition order:

/dev/sdba1 - NTFS (WinXP)

/dev/sdb1  ext3 boot (Gutsy)
/dev/sdb3  ext3
/dev/sdb2  Extended
/dev/sdb5  Swap


The /dev/sdb3 partition is the one I'm trying to boot from. I can't seem to find anything that will tell me what the (hd*,*) designation is for the /dev/sdb3 partition. (hd1,0) is Gutsy, so I guessed that the /dev/sdb3 partition would be (hd1,1). Before I couldn't get the kernel to load because the path was wrong, and that spelling error. When I corrected for both of those errors, then I got the mount error.

---

### Post by meierfra on 2007-10-27
/dev/sdb3  is (hd1,2)

---

### Post by GZBurtchell on 2007-10-27
> **meierfra said:**
> /dev/sdb3  is (hd1,2)


Just out of curiosity, how are you able to tell what partition is which between the sd** and (hd*,*)? I don't see the pattern to it. Or is there something I can run that will show me that kind of info?

---

### Post by meierfra on 2007-10-27
Grub starts counting at 0, So the hd numbers are just one less than the sd numbers. sda4  is (hd0,3), sdb8 is (hd1,7) and so on.

---

### Post by GZBurtchell on 2007-10-27
It got a little confusing with the extended and swap partitions listed on the partition information. The only ones I knew for certain that matched up with the /dev/sd numbers were (hd0,0) and (hd1,0).

(hd1,2) was the correct partition. I got it to boot up and start the installer. Unfortunately I didn't get far before it insisted on mounting the cd-rom drive and continuing the installation from cd.

---

