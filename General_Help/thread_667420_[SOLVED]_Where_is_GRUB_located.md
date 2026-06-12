---
title: "[SOLVED] Where is GRUB located?"
date: 2008-01-14
forum: General Help
---

### Post by rune0077 on 2008-01-14
Okay, so I want to remove Vista from my system (and run it through a virtual box from now on). However, when I run gparted I can see that my Vista partition is flagged for boot. Question is, does that mean that GRUB loads up from the Vista-partition, and if so, what happens if I format it and merge it with my Ubuntu-partition?

---

### Post by x1a4 on 2008-01-14
Hi,

The boot flag simply means that the partition is bootable.  What boots by default is determined in GRUB's menu file.  

GRUB is located in /boot/grub/ with a portion of itself (usually anyway) in the the MBR, wherever you installed it.  Typically it's okay to delete the windows partition without any adverse effects on Unbuntu.  But be sure to delete windows' menu entry from /boot/grub/menu.lst

---

### Post by p_quarles on 2008-01-14
I'm not an expert on booting, but I believe the boot flag is actually part of the system's partition table, which is also located in the MBR (the first 512 bytes of the HDD). Gparted is able to relocate that flag, but you do have to make sure than an existing partition is flagged as bootable. 

Agreed, btw, that you should delete the GRUB menu entry for Vista. GRUB can get grumpy when it looks for a non-existent partition.

---

### Post by rune0077 on 2008-01-14
Okay, I'll give it a try:

- only my Vista-partition is flagged as boot, so I'll reflag that to my Ubuntu-partition
- I'll edit the entry /boot/grub/menu.lst
- Then I'll remove Vista.

Hope it works. I'll report back when it's all over (if I don't, it's probably because I screwed up and threw my computer out the window (no pun intended) :))

---

### Post by p_quarles on 2008-01-14
Worst thing that can happen is that you'll need to dig up the Ubuntu live disk and reinstall GRUB:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

(okay, not really the worst thing; but the monitor self-immolating is considerably less likely ;) )

---

### Post by rune0077 on 2008-01-14
That didn't go as smoothly as one could have hoped for.

Managed to remove Vista without any hassle. But gparted did give me hassle when trying to resize my current partition. I put in the Vista installation CD, hoping that I could use Vista's partition manager for the job, but *that* deleted GRUB so I couldn't boot up.

Worse yet, I didn't have my Ubuntu-live CD. I did have an Open-Suse live CD, and I put that in and tried to reinstall GRUB, as per the thread referred above. GRUB now loads, and shows Ubuntu on the list (only Ubuntu since I deleted Vista), but when I select it, it refuses to start, saying something like "this entry doesn't exist" or some such. From Open-Suse (from which I'm currently writing this) I can see that my Ubuntu-partition still exists (using Open-Suse's partitioning thingy), and that it hasn't been deleted or reformatted or anything else. 

Now, how to get GRUB to recognize the Ubuntu-partition again? Well, I'll check back in a few minutes and then I'll post this in a new thread, since this is essentially a whole new problem.

---

### Post by kvonb on 2008-01-14
-

---

### Post by rune0077 on 2008-01-14
Here's the result of fdisk -l

```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
171 heads, 40 sectors/track, 114243 cylinders
Units = cylinders of 6840 * 512 = 3502080 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       89992      113242    79518420   83  Linux
/dev/sda2          113243      114243     3423420    5  Extended
/dev/sda5          113243      114243     3423400   82  Linux swap / Solaris

```

Which looks as it should for now. But when I try to run grub-install /dev/sda1, I get this:

```
Probing devices to guess BIOS drives. This may take a long time.
sed: can't read /boot/grub/device.map: No such file or directory
grep: /boot/grub/device.map: No such file or directory
/dev/sda1 does not have any corresponding BIOS drive.

```

---

### Post by p_quarles on 2008-01-14
What are the contents of the file /boot/grub/device.map? It should say something like this:
```
hd0 /dev/sda
```
That's verbatim what mine says -- correct for a single SATA hard disk.

---

### Post by kvonb on 2008-01-14
-

---

### Post by rune0077 on 2008-01-14
Ah, it was actually just a stupid mistake on my account. I forgot that Vista was installed before Ubuntu, so GRUB had the Ubuntu partition stored as hd(0,2), but after deleting Vista it was now located at hd(0,0). I made a quick change to /boot/grub/menu.lst, and am now back in Ubuntu. Thanks guys/girls/whatever you are, I am now Vista free (though planning on getting it up and running in Virtual Box).

Next issue: I have roughly 300 gigs of free space on my harddrive now that Vista is gone, so why won't gparted let me resize the Ubuntu-partiton? The option is greyed out. I'm guessing it's something to do with the drive being mounted.

OK, anyways, thanks all.

---

### Post by p_quarles on 2008-01-14
The drive shouldn't be mounted at all when running Gparted, and it would let you know if it were. The inability to partition free space is usually due to contiguity issues -- i.e., the free space isn't physically all on the same part of the drive. 

Basically, you may have to boot back into Gparted and attempt to move the partitions around so you can use the free space. It's been a while since I've done that, so unfortunately I don't remember exactly how it works.

---

### Post by rune0077 on 2008-01-14
Got it fixed. It took a looong time to grow the partition, but it's there now, Vista is gone, GRUB loads Ubuntu and all is good. Thanks again to everyone.

---

