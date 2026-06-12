---
title: "partition"
date: 2024-03-09
forum: General Help
---

### Post by larryb1607 on 2024-03-09
I shrank a partition I was planning to use for my Ububtu Cinnamon install.  The original partition was 849GB.  I shrank it by 60GB.  It took hours.  I had to leave the PC on overnight and when I came back to OS login screen was up.  This was an NTFS  partition.  I can see that the operation completed, but nothing I have used actually shows the space.  How do I get this so I can install to it and/or format it.

Thanks

---

### Post by oldfred on 2024-03-09
Best to use Windows to shrink NTFS partitions.
It may need chkdsk or defrag which can only be done from Windows.
Or you may have left the fast startup setting on when last used in Windows? That sets hibernation flag preventing Linux NTFS driver from fully seeing the NTFS partition.

---

### Post by larryb1607 on 2024-03-09
I suppose I could make an backup image of the drive and then do what I want with the drive and install the image.

---

### Post by yancek on 2024-03-10
There is no reason that simple process would have taken hours.  I agree that if you want to resize a proprietary windows filesystem partition, you use windows and reboot and run chkdsk after.  You have an unusual setup with Linux partitions on the old Legacy type system from the 1970's and an ntfs partition.  Do you now have an Ubuntu or other Linux install as you show Linux filesystem partitions in your image.  You indicated you rebooted and and saw the OS login, which OS?  Ubuntu already installed, windows?  Do you have windows installed or is that just a data partition you share with windows users?  If you have windows, which release?  The suggestions in post 2 are the most common reasons for this problem so try those first.

---

### Post by TheFu on 2024-03-10
> **larryb1607 said:**
> I shrank a partition I was planning to use for my Ububtu Cinnamon install.  The original partition was 849GB.  I shrank it by 60GB.  It took hours.  I had to leave the PC on overnight and when I came back to OS login screen was up.  This was an NTFS  partition.  I can see that the operation completed, but nothing I have used actually shows the space.  How do I get this so I can install to it and/or format it.

Thanks

I suspect the task failed.  Use MS-Windows to shrink MS-Windows file systems.

BTW, the way that HDD is setup is odd.  1 primary partition with logical partitions inside it - that's just odd.  Normally, there would be 2-3 primary partitions with only 1 being "extended".  Looks like the Windows install is  really, really, old and not using UEFI to boot.  That goes back to Win7 days.  You could take this opportunity to do some important maintenance.
a) Replace the HDD with new.  This way, you are working in completely new storage and don't risk the current setup.
b) Reinstall MS-Windows, then Linux using UEFI and GPT.   GPT doesn't need extended partitions. However, MS-Windows mandates UEFI to have access to GPT. Also GPT doesn't have a 4 primary partition limitation.  Over 100 primary partitions are possible under GPT.
c) During the re-installations, size the storage how you actually need it.

Now you have a new HDD and a place for backups. That's a good thing.

If you've been using Linux more and more, you might consider using a _volume manager_ like LVM to make disk management much more flexible, but slightly more complex. Dual boot makes setting up LVM harder. I've never done it, but if you setup the OSes with minimal sized storage, then you'll be able to manually add LVM to a new, empty, fairly large, partition.  Just an option.

There are lots of options. Instead of dual booting, you could place on the OSes into a virtual machine and let 1 OS manage all direct hardware access.  I've been doing this since 2006.  It removes all sorts of complexities and make the computer very flexible.

Just providing a few other options to be considered.  Each has good and bad aspects.

---

### Post by larryb1607 on 2024-03-10
Maybe I confused myself as I have another post in this forum called "new install".  My main machine is a Win 7 laptop.  I have an external HDD I bought for backup.  The external HDD is what is shown in the picture.  It is formatted as NTFS.  A while back I decided to try Linux.  I created a partition for it and installed the Ubuntu based version on the 2 ext4 drives.  The system I have been using has been giving me some problems and the website support is not too good at times.  I decided I wanted to try an actual Ububtu based system and slowly migrate the data from the other Linux system.  I used G[arted in the other Linux system to shrink the NTFS drive where I was hoping to create a partition for Ububtu Cinnamon.  I can see where using Gparted was a mistake, but once started was worried about canceling.  I use an external HDD for Linux as it is portable and I have a desktop as well.  In my other post, I was worried about having 2 boot partitions.

---

### Post by yancek on 2024-03-10
Did you use any tutorial to resize the partition with gparted?  Doing this even with an ntfs filesystem should work but using windows tools to modify a windows partition should work better.  Did you use the Gparted Manual (link below) and instructions there?  Definitely the best site to use for gparted and it's been on line and available for many years.

[https://gparted.org/display-doc.php%3Fname%3Dhelp-manual](https://gparted.org/display-doc.php%3Fname%3Dhelp-manual)

---

