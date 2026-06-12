---
title: "[SOLVED] GRUB issues"
date: 2007-09-25
forum: General Help
---

### Post by igeterrors on 2007-09-25
This is silly, but I actually have a tri-boot system: Windows XP, Dapper, and Feisty.  I originally installed Dapper alongside Windows and was a dual booter for a while, but when I decided to take the plunge to Feisty I was too chicken to overwrite my Dapper install, so I created a new partition and installed Feisty there.  

All was well until I made some changes to the partitions (with GParted) to reallocate free space (what with having 3 OSes and all) amongst the filesystems and at first I must've done something wrong because I got GRUB error 17, but I've seen that before and I just pulled out my Super Grub Disk and restored the MBR and everything seemed OK.  I can boot into Windows, I can boot into Dapper, but then I realized there's no sign of my Feisty kernel in the GRUB list.  I think it was 2.6.20.  Problem is I can't remember which partition I had set to boot Feisty from.  I believe I created separate /home, /usr and maybe /boot partitions and while I can probably guess, I don't know for sure which is which and anyway I don't want to do anything crazy without checking with you guys first.

Any help, suggestions, what to do first, etc? Thanks.

---

### Post by por100pre1 on 2007-09-25
Login to Dapper. Check your partitions:

```
sudo fdisk -l
```

Locate menu.lst and take a look at it.

```
locate menu.lst
```

---

### Post by igeterrors on 2007-09-25
Thanks, that was definitely my first thought, too, but as I mentioned, there's no sign of my Feisty kernel in menu.lst.  I'm trying or hoping to get it back, or at least find out what changes I need to make to menu.lst so that I can boot back into Feisty.

---

### Post by por100pre1 on 2007-09-25
Try using my Feisty entries as a reference:


```
title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=37b42cdd-a149-49b6-8c0d-0eba0d50039a ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b42cdd-a149-49b6-8c0d-0eba0d50039a ro quiet splash locale=es_ES
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=37b42cdd-a149-49b6-8c0d-0eba0d50039a ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet
```

Use Gparted to check your drive and check your hdd settings, partitions, etc.

Mount Feisty partition and look at /boot folder. There you will see which kernel versions you exactly have.

---

### Post by fjgaude on 2007-09-25
Don't forget, you have two grub menu.lst files, one for Dapper and another for Feisty. Find the Feisty one by mounting the partition you think it is on, then copy the menu.lst from there to the Dapper menu.lst. Mkae sure you use the correct hd0,x partition. <smile>

You can find all your partitions using Gparted, or use:

> sudo fdisk -l

As we upgrade the kernel we seem to go from one menu.lst to another

---

### Post by por100pre1 on 2007-09-25
> **fjgaude said:**
> Don't forget, you have two grub menu.lst files, one for Dapper and another for Feisty. Find the Feisty one by mounting the partition you think it is on, then copy the menu.lst from there to the Dapper menu.lst. Mkae sure you use the correct hd0,x partition. <smile>

You can find all your partitions using Gparted, or use:

```
sudo fdisk -l
```

As we upgrade the kernel we seem to go from one menu.lst to another

Yes, and use the UUID of your feisty partition.

---

### Post by igeterrors on 2007-09-25
Well this seems odd.  When I 
```

~$ sudo fdisk -l

```
 I get 

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2663    21390516    7  HPFS/NTFS
/dev/hda2            8274        9573    10442250   83  Linux
/dev/hda3            9574        9729     1253070   82  Linux swap / Solaris
/dev/hda4            2664        8273    45062325    5  Extended
/dev/hda5   *        7637        8273     5116671   83  Linux
/dev/hda6            6107        7636    12289693+  83  Linux
/dev/hda7            2920        6106    25599546   83  Linux
/dev/hda8            2665        2919     2048256    b  W95 FAT32

Partition table entries are not in disk order

```

(I set the boot flag myself in Gparted *after* all the trouble started.)

But then when I 
```
~$ sudo mount -r /dev/hda5

```
I get
```
mount: can't find /dev/hda5 in /etc/fstab or /etc/mtab

```

---

### Post by igeterrors on 2007-09-25
In case anyone's wondering, it's ```
sudo mount /dev/hda5 /mnt
```  not ```
sudo mount /dev/hda5
```if you want it to work, anyway.  : )

So I found my menu.lst file -- the /boot dir was not where I thought, so go figure. Turned out to be in hda7, not hda5.  So now let's see if I can boot into Feisty...  I'll report my results here.

---

### Post by igeterrors on 2007-09-25
And the results are... failure!  The Feisty kernel shows up in the GRUB menu now but when I select it and try to boot I get error 15 -- file not found. 

Looks like I've finally hosed the system but good.

---

### Post by igeterrors on 2007-09-26
lest i be forgotten...

---

### Post by confused57 on 2007-09-26
What you can try is boot into Dapper, open a terminal, check the output of:
```
sudo grub
find /boot/grub/stage1
```
this should show Feisty's root(or boot) partition.

Then you "should" be able to add a configfile entry to boot Feisty, for example:
```
title  Feisty
configfile (hd0,6)/boot/grub/menu.lst
```

This guide explains configfile booting:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by igeterrors on 2007-09-26
Yeah!!  That did it.  Well actually what did it was that by writing "hd0,6" in your post, you helped me notice that my menu.lst file still had the Feisty partition as hd0,7.  I guess I was just looking to get the Feisty entry back into the file and didn't read it carefully.  

A tip for others: Once you have determined (as described above) the cause of the problem, *don't* do this:

[LIST]Log into Dapper (assuming it's your Feisty partition you're trying to log into)[/LIST]
[LIST]Make the changes to the *Dapper* menu.lst[/LIST]
[LIST]Reboot[/LIST]
[LIST]See that it didn't work[/LIST]
[LIST]Swear and curse[/LIST]

Instead do *this:*

[LIST]Log into Dapper.[/LIST]
[LIST]Mount the *Feisty* partition.[/LIST]
[LIST]Change the *Feisty* menu.lst[/LIST]
[LIST]Reboot[/LIST]
[LIST]See that it worked[/LIST]
[LIST]Pump your fists in triumph[/LIST]

Thanks, Confused57.  You may be confused, but I was downright befuddled.  : )

---

### Post by hexstar on 2007-09-26
When constructing hd0,0 take note that the first zero represents the hard drive with the first hard drive starting at 0, next one at 1, etc...same rule for the second 0 which represents the partition on the given hard drive :)

---

### Post by igeterrors on 2007-09-26
> **hexstar said:**
> When constructing hd0,0 take note that the first zero represents the hard drive with the first hard drive starting at 0, next one at 1, etc...same rule for the second 0 which represents the partition on the given hard drive :)
Somehow the numbers got off by 1.  The Feisty boot partition was hd0,7 before I altered the filesystems and then afterward it was hd0,6.  Not exactly sure why...  I guess I deleted a partition and/or combined two partitions into one?  Either way, it's odd that Gparted doesn't update the menu.lst file to account for the change.  Right?

---

### Post by hexstar on 2007-09-26
I don't believe gparted normally does that. Gparted simply takes care of non destructive partitioning tasks and that's it, it's up to the end user to then make the appropriate changes with their bootloader.

---

### Post by igeterrors on 2007-09-26
> **hexstar said:**
> I don't believe gparted normally does that. Gparted simply takes care of non destructive partitioning tasks and that's it, it's up to the end user to then make the appropriate changes with their bootloader.

Leaving something like that up to me (esp. *without telling me* that it's being left up to me) is a VERY bad idea... : )

In fact, I'll go further and say that leaving something like that up to me is the OPPOSITE of non-destructive. : )

---

