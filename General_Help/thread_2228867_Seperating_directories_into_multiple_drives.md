---
title: "Seperating directories into multiple drives"
date: 2014-06-10
forum: General Help
---

### Post by Tristan_Williams on 2014-06-10
I remember reading somewhere that it would increase system performance if certain directories like /var were on separate drives.

So let's say I can buy as many SSDs as I want. What would be the best way to arrange the directories on 3 or 4 SSDs?

An example could be:
-Drive 1 = /home and /usr
-Drive 2 = /bin, /boot, /sbin, /tmp, and /var
-Drive 3 = /dev, /etc, /mnt, /proc, /sys, and /tmp
-Drive 4 = everything else

I know the above is probably completely wrong... So what would be the "optimum" way to arrange them?

---

### Post by Impavidus on 2014-06-10
/dev, /proc and /sys are pseudo-filesystems. They don't need disk space or partitions.
/bin, /sbin and /etc (and /root) have to be on the root partition, as these have to be available before other partitions are mounted.
/boot is interesting if you use LVM (usually on encrypted drives), as the kernel has to be loaded from /boot before LVM partitions can be mounted (I think). Once loaded, the kernel resides in memory and /boot is no longer accessed.
/mnt shouldn't contain any data, but only a few mount points for other partitions, or it is used itself as a mountpoint.
Some people place /tmp in ram. This is fast and /tmp is cleared on reboot anyway. You need enough ram for this of course.
Other partitions might be interesting. Can't say whether your boost will be significant, but you can try.

The idea is that you take advantage of the fact that the bus is faster than the disk, but it only helps if you simultaniously access data on different disks. The most accessed parts are usually /usr, /home and /var, but depend on your computing habits. There can be other reasons for using separate partitions or even disks, like optimisation for fast read or write access, for large numbers of small files or few big files, sharing data between different computers or operating systems, reducing write cycles. There can also be reasons not to do so, like fragmented storage space.

---

### Post by oldfred on 2014-06-10
I believe in reliability over speed. So I configure every drive so it can boot and have everything on my SSD that I need to boot with. But then all data is on slower hard drive as data is not accessed as often.

If you have lots of RAM, Linux caches recent activity in RAM so reuse automatically occurs. Only if you load another new application and there is no unused space will something be released.

So I have all of / including /home in my SSD and it uses 11GB. My /home is 2GB and almost all of that really is .wine for Picasa as that is the only larger hidden folder in my /home that I have not moved to my data partition on hard drive.

This says SATA and AHCI are not fast enough for the new extremely fast SSD.
[http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826.html](http://www.tomshardware.com/reviews/samsung-xp941-z97-pci-express,3826.html)

---

### Post by The_Riskbreaker on 2014-06-19
So, in an attempt to avoid post duplication, let me clarify. I'm buying a new laptop like the posters that has a small 120GB SSD, and a larger terabyte HD. if I install everything but /home on the SSD, and put home on my terabyte drive, that would work the best, right? I don't want to pay for the smaller SSD if it's not going to benefit me.

Edit: I had a previous user on the forums, but that was 2+ years ago and I decided it'd be easier to make a new one. I am also currently studying for the Linux+/LPIC-1 but I am not 100% sure on the issue of what directories need to be on the same drive.

---

### Post by oldfred on 2014-06-19
There are many ways to configure system and none are really wrong as long as you understand some of the advantages or disadvantages or your configuration. But whatever you use good backup procedures are required.

I prefer reliability, so I have both / (root) and /home inside / on my SSD. So SSD will boot even if I have issues with hard drive. I also have another full install (or 3) on hard drive which I could boot in an emergency.

But some want speed and even used multiple SSDs with parts of system on each or even RAID 0 which if any drive fails causes complete loss of data, but can be very fast.

It is easier for a newer user to configure / on SSD and /home on hard drive as you do the entire configuration during install.
It is a bit more advanced to have just data partitions on hard drive as you have to create mount points after install, edit fstab to mount the data partitions to mount points and link or configure data folders to be in your /home.

---

### Post by The_Riskbreaker on 2014-06-19
I store a lot of files in my home directory; music, videos, etc... But I just had the lightbulb moment, and realized I don't need to store them on the SSD. Can't you take the Music, Video, Pictures, and other directories out of Home and put them on a separate drive? I mean, aside from hidden files and some other essentials, does the Home folder need to contain the Doc, Music and other folders? Apologies if this is a newbie question. I checked my LPIC-1 book and some links, but came up dry.

---

### Post by oldfred on 2014-06-19
I originally started that process when dual booting Windows XP and trying to learn Ubuntu. My wife wanted to check email and wanted same Firefox bookmarks, so I had to reboot all the time. Then found I could create a shared then fat32 but now NTFS data partition and put profiles into the shared partition. Then Firefird and Thunderbird were almost identical in both systms and data was the same.

I now have two data partitions. Even though not booting XP anymore I have not converted NTFS partition data over, but all new data goes into my Linux formatted data partition.
I create a mount like /mnt/data and /mnt/share (NTFS) and mount my partitions on the hard drive into my system on SSD. Then I link folders from mount into /home so I have the same folders but they really are in my data partition.

       The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

