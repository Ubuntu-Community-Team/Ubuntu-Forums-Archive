---
title: "Hard drive - wrong size reported"
date: 2007-05-21
forum: General Help
---

### Post by floke on 2007-05-21
I am having to reformat my hard drive (long story) - its 80G but the ubuntu partitioner is only reporting it as 74G - what's happened to the missing 6Gigs?

-- A seperate question (related to the reason I'm having to reformat) - tried to install PCLinuxOS but it has borked my partitions - nothing boots anymore and the ubuntu LiveCD reports the hard drive as empty - but the PCLOS live CD can detect the partitions - any thoughts on this?

Cheers for any help

---

### Post by DoctorMO on 2007-05-21
Seems like not a problem, my hard drive is a 250GB West Digital yet there are only 240GB for use and the reason for this is:

Hard Drive makers get away with false avertising, the computer world counts up in 1024 but the hard drive makers count up in 1000, so in the real world 1024 bytes = 1KB and 1024KB = 1MB so 1024MB = 1GB etc but the hard drive makers it's 1000 bytes = 1KB, 1000KB = 1MB etc which is clearly wrong. so what you have there is an 80,000,000,000 byte drive which works out in the real world as 74.505GB

Evil isn't it.

As for your partitions, there are very good programs which are more in depth but allow you to debug your partition table, try learning how to use fdisk (command line) it will help you by showing you exactly what is on your drive.

Only this weekend we had a drive that reported the first partition as NTFS even though it was formatted as ext3 (royally wrong) but for some reason gParted just failed to fix this problem and instead would just break,

---

### Post by floke on 2007-05-21
Thanks, that explains issue #1

As for issue #2 - PCLinuxOS is refusing to boot up (its on sda1) - i've added my ubuntu partition to the PCLOS Grub so now I can boot into ubuntu - but when I run ubuntu off the LiveCD the GParted utility does not recognise any of my partitions (sda1-7). Instead it just reports an unallocated block of 75Gs. If I mount my hard drive and run fdisk -l then I can see all of my partitions clearly.

Any idea what's going on?

---

### Post by smoker on 2007-05-21
hi,

i've had problems with the gparted on the ubuntu cd before, and since i've downloaded and use the gparted live cd which i've never had any probs with, if you want to give it a try [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) 

can i ask what file system pclos used when it installed? sometimes i think this is where the ubuntu gparted fails, if it has to deal with different file systems, even though it should not.

best of luck

---

### Post by floke on 2007-05-21
I think it's ext3 - but it could have been reiserfs. In any case PCLOS won't boot from my HDD even though it runs fine from LiveCD. My solution was to reinstall Feisty over the entire hard drive - drastic, but my partition table was a mess and I needed it to be far less ad hoc and more logical - so its all sorted for now (until I try to install sabayon tomorrow, perhaps!). I don't use Gparted on 7.04 since it has a strange habit of mounting partitions halfway through working on them; so use the 6.10 version instead: it was weird since it saw the whole HDD as unallocated, even though I could see the partitions through fdisk -l.

Anyway, thanks for the help.

---

### Post by ghell on 2007-05-21
> **DoctorMO said:**
> Hard Drive makers get away with false avertising, the computer world counts up in 1024 but the hard drive makers count up in 1000, so in the real world 1024 bytes = 1KB and 1024KB = 1MB so 1024MB = 1GB etc but the hard drive makers it's 1000 bytes = 1KB, 1000KB = 1MB etc which is clearly wrong. so what you have there is an 80,000,000,000 byte drive which works out in the real world as 74.505GB

Evil isn't it.Indeed it is, I used to get a lot of people telling me that windows was "stealing" their hard drive space.

It's not actually false advertising though, 80GB = 80*10^9 = 80,000,000,000 bytes. 80GiB = 80*2^30 = 85,899,345,920 bytes. What a difference an i makes.

---

