---
title: "linux disabled other o/s"
date: 2008-01-01
forum: General Help
---

### Post by bjdburton on 2008-01-01
i just installed linux and it is brilliant. i have come across only one problem. i have xp and ubuntu installed. (i require xp as i do a lot of sound work. i use sibelius, cubase and reason) the wine support, although good, does not support reason properly as there is no way of installing asio drivers. linux has locked me out of windows. i can no longer get onto windows as it tells me that windows has been disabled. the only thing i have done recently to come across this problem is install linux and wondered if anyone has any suggestions.

the exact screen i get when trying to access windows is:
[IMG]http://i260.photobucket.com/albums/ii10/bjdburton/P1010036.jpg[/IMG]

---

### Post by taurus on 2008-01-01
Disabled.  Do you mean you can't boot windows anymore or do you mean you can't access windows partition from Ubuntu?

---

### Post by bjdburton on 2008-01-01
the partition is there but when i hit enter the screen i have just added to my original post pops up. thanks for the quick reply

---

### Post by meho_r on 2008-01-01
Did you install Linux onto a partition which is after Windows partition? I once had similar problem and realized that Win should be on the first primary partition.

---

### Post by ~LoKe on 2008-01-01
Linux isn't really at fault here.  However...the partitioner could have have faulted and slightly...skewed your Windows partition.  I'll do some googling.

---

### Post by ~LoKe on 2008-01-01
A quick search brought this up:

> Just solved this one for my situation. I found information elsewhere that your NTFS or FAT32 partition can become marked 'hidden' in this Linux/Windows mess. Using the Partition Magic boot floppies I selected my 'hidden' NTFS partition, went to 'Advanced' and I believe it was 'unhide'.
After that, GRUB would start both Fedora and WinXP with no problems.

It's dated 05/2005, so I'm not sure if that's still an issue.  If it turns out that it's severely messed up, you cold always pop in the Windows XP CD and run the repair installer.  Have you tried booting into safe mode?

> I soon realised this as far as FC4 was concerned and fixed it using command line grub, but since I hadn't booted into Windows for a few days I forgot about unhiding some partition that Windows needed to see once it started up. Hence the blue screen.

In summary, before you reach for any recovery disks, emergency boot disks, Windows installation CD or impact maintenance tools, try entering this at the grub command line:

unhide (hd0,0)
unhide (hd0,1)
unhide (hd0,2) .. and so on until you run out of partitions.

My Windows and FC4 are now both booting happily, and I didn't have to go anywhere near the Ghost image I made before starting the FC4 upgrade process. Which, by the way, is a practice one highly recommends. 

---

### Post by bjdburton on 2008-01-01
windows is on the first partition. if i try and reinstall windows from the disk it tells me exactly the same. that the use of windows has been disabled. i have also just checked and the partition is not set to hidden.

---

### Post by ~LoKe on 2008-01-01
> **bjdburton said:**
> windows is on the first partition. if i try and reinstall windows from the disk it tells me exactly the same. that the use of windows has been disabled.

Try the grub method and see if your windows partitions are hidden.  I've never come across this since using linux, so I believe it's no longer an issue, but it can't hurt to try.

---

### Post by bjdburton on 2008-01-01
yep. i just unhid all of the partitions using the grub method. still no luck lettin me use windows

---

### Post by ~LoKe on 2008-01-01
When and where does it actually say Windows is disabled?

---

### Post by bjdburton on 2008-01-01
when i select windows xp at the grub boot loader i get the screen shown in the original post and when i try to reinstall xp using the disk it wont let me

---

### Post by geirha on 2008-01-01
What's the output of ```
sudo fdisk -l
```?

---

### Post by bjdburton on 2008-01-01
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8e378e37

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            1840        9729    63376425    b  W95 FAT32
/dev/sda2   *           1         620     4980118+   2  XENIX root
/dev/sda3             621        1839     9791617+  83  Linux

---

### Post by geirha on 2008-01-01
hm, the windows partition is at the end of the harddrive, and /dev/sda2 has the boot flag.  Try to give the windows partition the boot flag.
 
What's /dev/sda2 btw? never seen a XENIX partition before ...

---

### Post by ~LoKe on 2008-01-01
> **geirha said:**
> What's /dev/sda2 btw? never seen a XENIX partition before ...

I was about to reply and then I saw that as well.  Time to go to Google!
> Xenix was a version of the **Unix operating system, licensed by Microsoft** from AT&T in the late 1970s.
AHHHHHHHH!!!!

---

### Post by bjdburton on 2008-01-01
the one you asked about is a recovery partition

---

### Post by RC Howe on 2008-01-01
That may mean that you are booting from your recovery partition. I once had a problem after messing with my boot flags and it would not let me boot anything. Try:
1. Removing the flag from your recovery partition
2. Adding the flag to your windows partition

---

