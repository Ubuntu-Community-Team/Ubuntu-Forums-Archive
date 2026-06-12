---
title: "Move Ubuntu (/) to SSD"
date: 2013-04-19
forum: General Help
---

### Post by SnoopFogg on 2013-04-19
Hi, I've have a dual boot system (Windows and 12.04) and just installed an SSD for the OS's.  What is the easiest way to move the Ubuntu OS (/) to the new SSD?

On the old HDD I have a primary partition sdc2 with extended partitions sdc5-7):

/dev/sdc2
      /dev sdc5 - /home (250 GiB)
      /dev sdc6 - / (20 GiB)   
      /dev sdc7 - /swap (7.5 GiB)

I also have primary partition /dev/sdc3 (500 MB) which is flagged "boot" (though that might be windows?)

I want to move sdc6 to sda2 (on the SSD) though there is only 19.24 GiB space on it.

Any suggestions?  Would it be easier to do a fresh install on the SSD, then link to sdc5 for /home?

Cheers

---

### Post by sudodus on 2013-04-19
I think you can boot from another drive, for example your Ubuntu install CD/DVD/USB drive and use **[FONT=courier new]rsync[/FONT]** to copy the files in the root partition to a partition on the SSD. This works if the target partition is smaller, but there is still space for the files. Run

```
 sudo blkid
```

 Then you need to change the content of **[FONT=courier new]/etc/fstab[/FONT]** to point to the new root partition's UUID. This needs to be fixed manually also in /boot/grub/grub.cfg, so that grub will find the new location of the root partition. When it does, you can use

```
sudo update-grub
```

and create a new [B][FONT=courier new]/boot/grub/grub.cfg
[/FONT][/B]
*Edit*: I suggest that you also add the mount options**[FONT=courier new] noatime,discard [/FONT]**to the root partition entry in[B][FONT=courier new] /etc/fstab
[/FONT][/B]

---

### Post by oldfred on 2013-04-19
While you can use several methods to copy, you have to edit fstab and reinstall grub2's boot loader.

I prefer the clean install option, but use manual install or Something Else and choose to mount existing /home but DO NOT format it. 

I actually have /home inside my / (root) on the SSD, but have all files & folders that are my data in data partitions on hard drive and link the data back into /home on SSD. I also move some hidden folders like Firefox & Thunderbird profiles to hard drive so I can easily share with mulitple installs.

---

