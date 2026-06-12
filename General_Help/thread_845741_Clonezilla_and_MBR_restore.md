---
title: "Clonezilla and MBR restore"
date: 2008-06-30
forum: General Help
---

### Post by geo909 on 2008-06-30
Hello everybody,
I often make backups of my hard disk partitions using clonezilla.
I had a problem and I restored a partition today. However, grub couldn't start, that is, clonezilla hadn't saved the MBR (am I correct?)

Is there -in general- a way to say to clonezilla to backup the MBR too
when you backup your partitions?

Thanks a lot in advance!

---

### Post by hyperair on 2008-06-30
I don't think so, because MBR isn't part of a partition unless I'm mistaken. what you can do is just remember a few grub commands so you can restore it if necessary. From a LiveCD, run:
```
sudo grub
```

Then a grub prompt will appear. First, search for /boot/grub/stage1
```
find /boot/grub/stage1
```
It should return something like:
```
(hd0,2)
``` or something of that sort. Then you setup grub.
```
root (hd0,2)
setup (hd0)

```
What this does is it sets the third partition of the first hard disk as the grub root, and then writes the bootloader to the MBR of the first hard disk.

---

### Post by geo909 on 2008-07-01
So, you have to reinstall grub after using clonezilla?
I have always found that more complex than it is said to be.

For example, I used super grub disk and all the ways to restore grub 
failed.

Also, I try what you said on my suse machine and when I do
```
jorge@linux-kupy:~> find /boot/grub/stage1

``` 
I just get
```
/boot/grub/stage1
```

---

### Post by hyperair on 2008-07-01
Do it in the grub prompt! Not in the terminal. I asked you to run "sudo grub" to get a grub prompt didn't I?

Also, it's not a case of "reinstalling" GRUB. It's a case of updating your MBR to the correct settings.

---

### Post by geo909 on 2008-07-01
> **hyperair said:**
> Do it in the grub prompt! Not in the terminal. I asked you to run "sudo grub" to get a grub prompt didn't I?

Also, it's not a case of "reinstalling" GRUB. It's a case of updating your MBR to the correct settings.

Yes you were right!
Ok, I understood now..

I'll try it and tell you had happened

---

### Post by komputes on 2008-07-26
Well I just had to sacrifice the data on my hard drive so I started off clean and decided that it was time to test clonezilla.

I created a dual boot XP/Ubuntu with absolutely nothing installed other than the base operating systems. I booted into both OSs and everything was fine. So I backed up the device -> image to another computer via ssh. Then I completely erased the HDD and attempted a restore.

To my surprise, the grub screen had changed to a version installed by clonezilla. The grub menu still displayed XP & Ubuntu, but would not boot into the XP NTFS partition.

At that point I was unable to boot into the second part of the XP installer, I kept getting an error "No operating system found" Ubuntu installed well, but I was unable to boot install or boot into windows. Grub was pointing to the correct partition (hd0,0) but it would not boot. 

I tried restoring the mbr/bootloader within XP recovery console but nothing seemed to work. Since you guys have experience with clonezilla, are there known issue for backing up a dual boot drive?

As well, are there any other projects that have the same goal as cloning a drive for easy recovery?

---

### Post by hyperair on 2008-07-27
Honestly speaking, I have never used CloneZilla before, and don't think I'll ever use it. I've used dd all the while. No user interface, but hey you can get a perfect dump of whatever storage medium you were using. If compression is needed, then gzip, or bzip2 the image.

---

