---
title: "Help wanted with data partition..."
date: 2014-07-14
forum: General Help
---

### Post by Mike_Walsh on 2014-07-14
Afternoon all.

I would like a bit of advice with creating a new partition.

I have a dual-boot config on my desktop PC. I have Ubuntu 14.04 on the larger partition (/dev/sda1), and Zorin's OS 8.1 Ultimate 64 on /dev/sda6.

What I would like to do is to create a separate partition to contain all my data files, but I don't know quite how to create it so it can be accessed by both OSs. I have enclosed a screenshot of GParted, showing the current 'state of play'.

I'm still fairly new to Linux (3 months and counting!), although I'm quite an old hand with computing in general.....though most of that was with Windows, and I don't have that much experience with disk admin stuff.

Any help would be much appreciated.

Regards,

Mike.

---

### Post by sudodus on 2014-07-14
0. Shrink **/dev/sda1** to create unallocated space for the data partition.

1. With only linux in the computer, I suggest that you make a [primary] partition with an **ext4** file system.

2. Consider if you want to ***automount*** the partition, or if you want to mount it manually. Automounting would require an entry in **/etc/fstab**

---

### Post by oldfred on 2014-07-14
+1 on sudodus' suggestion.

More info and some links on details:
 I prefer a separate /data partition. Then you can easily share your data without having the conflict of the user settings in hidden files & folders. Works best if all installed systems are Debian based, see UID issues below.

   The actual user settings are small. My /home is 2GB with most of that as .wine with Picasa which I have not yet moved to my /data. Because /home is small I now keep it as part of / (root) which is a total of 11GB with /home.
Then I can have a fully functioning system on one drive but have data linked in from other partitions on other drives.

   Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[URL="http://ubuntuforums.org/showthread.php?t=2192848"]http://ubuntuforums.org/showthread.php?t=2192848

[/URL] Shared Data with Different operating systems, different uid and gid issues - Morbius1
[http://ubuntuforums.org/showthread.php?t=1675381](http://ubuntuforums.org/showthread.php?t=1675381)

[URL="http://ubuntuforums.org/showthread.php?t=2192848"]
[/URL]

---

### Post by Mike_Walsh on 2014-07-14
Hi, guys.

Thanks for your replies. I've been reading up about this, but I'm still a bit lost. However, I was thinking about 'linking' folders in from other 'drives' (or, as in this case, partitions); certainly sounds like one way to do it.

Do I take it that what you're doing is creating a Home folder of what is essentially links? If that's the case, then I do have experience of doing something similiar when I was running Win XP. It's just taking me a little while to get the hang of the different terminology, and the way that the kernel, etc., is constructed.....and the way it all works!

Regards,

Mike.

---

### Post by oldfred on 2014-07-14
You mount the partition(s) with fstab to have them permanently mounted at the same location.
Then you link folders in the partition.
If Linux formats you have to also set ownership & permissions to give yourself permission to use the partition(s).

I originally started with a NTFS data partition for sharing with my XP install. But now that I do not use XP all new data goes into my Linux formatted data partition. I still have the NTFS, but after next major hardware change will obsolete it.

---

