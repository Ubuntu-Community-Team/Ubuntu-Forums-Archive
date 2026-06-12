---
title: "Old motherboard, no UEFI and a large harddrive (MBR vs. GPT)"
date: 2016-11-29
forum: General Help
---

### Post by andrewsc0 on 2016-11-29
Over the weekend I took a little effort to upgrade my old desktop and ordered some more ram, a 240 gb ssd and a 5tb hdd.

As I am reading up on doing fresh installs of ubuntu (its been nearly six years) using two harddrives (never done that before) I learned about the difference in MBR and GPT partitions. Of course a gpt partition requires UEFI boot as opposed to old fashioned bios. My motherboard was bought (and likely not the latest model at the time) in 2010, UEFI became standard in 2011 and as far as I can tell the mb does not have UEFI on it. (here is the model MB [http://www.newegg.com/Product/Product.aspx?Item=N82E16813128411](http://www.newegg.com/Product/Product.aspx?Item=N82E16813128411)).

My question is: Is there still a way for me to use a GPT partition and UEFI on this old motherboard? If not, what are my options to take full advantage of the 5tb hdd that is currently being shipped to my home? I would prefer the answer to not be buy a new motherboard and cpu, it was difficult enough to get me to pull the trigger on the three above purchases.

Thanks

---

### Post by &amp;KyT$0P# on 2016-11-29
> **andrewsc0 said:**
> Of course a gpt partition requires UEFI boot as opposed to old fashioned bios. 
Er, no it doesn't.  Just two weeks ago I installed Xubuntu 16.04 on a friend's old Dell desktop - older than yours.  I partitioned the disk as GPT and it works fine.

All you have to do is be sure to create a [BIOS boot partition]("https://en.wikipedia.org/wiki/BIOS_boot_partition") at the start of the disk.  Put a 1-2 MB unformatted partition as the first partition on the disk, and set it "bios_grub" flag, **before** installing Ubuntu.

No EFI needed.

---

### Post by andrewsc0 on 2016-11-29
That's wonderful news! So i can format both the ssd and the hdd with gpt and then use the following as my partition table?

so instead of say a /boot partition I would have:
partition one as: the 1-2MiB partition set as bios_grub
partition two as : / (say 40gb)
partition three as : /swap (16gb. I know its not necessary, but I do use hibernation and I'm not planning on storing anything on the sdd so I have plenty of space)
partition four as: /tmp (10gb)
partiton five as: /var (10 gb)
partition six as: /home for the rest

Do I need to name the partition that is the 5tb hdd anything or just format it?


and then create symbolic links for all of my files to store on the hdd?

---

### Post by Dennis N on 2016-11-29
Is there a reason for the separate /var and /tmp? Most users don't do that. Could lead to space availability problems. At most, / and a separate home partition. (I use just /  and swap and have a separate data partition for my work files. This is on a separate disk.)
You can label the filesystem on you 2nd disk after installation if you want.
I only use bookmarks (shortcuts) to my data folder on the 2nd disk, not symbolic links. But you could use links - your call. 

What IS true about GPT and UEFI is that UEFI requires a GPT partitioned disk. So you had it reversed.

---

### Post by andrewsc0 on 2016-11-29
There really isn't reason for the separate /var and /tmp. From what I gather I wouldn't really ever use /var but from experience working with photos (which is the primary use of my desktop) my /tmp file can become fairly large at times, perhaps even more reason to leave it within its own folder on /. Should I increase the size of / if I'm not going to use /var and /tmp?

When you say you use a separate data partition is that different than /home? 

Would it just be easier to do the following:
on the ssd:
bios_grub
/ (say 60gb)
/swap (16gb)
leave the rest empty and then make the entire hdd
/home

would that work?

---

### Post by Dennis N on 2016-11-29
60 gB for / should be enough. I only allow 25-30 mB for / and that includes my home partition. All my stuff is in the data partition on the 2nd disk, so that is my largest. The 2nd disk is 500gB and I allocated about 120gB for data - more than enough for me. I can easily expand it should I ever need to.

I use a separate data partition because I multiboot several Linux OSes. Each OS mounts that same data partition when it is being used and accesses the same files. 

Here is the setup. sdc is just a usb flash drive that happens to be plugged in right now so it got picked up. Each 25G partition is another OS - all Linux. The 80M partitions are all EFI system partitions, as this is a UEFI computer. sdb contains my data partition (mounted at "/mnt/Common-Files").

```
[dmn@Zotac ~]$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT
sda      8:0    0 232.9G  0 disk 
&#9500;&#9472;sda1   8:1    0    80M  0 part /boot/efi
&#9500;&#9472;sda2   8:2    0  24.4G  0 part 
&#9500;&#9472;sda3   8:3    0   3.9G  0 part [SWAP]
&#9500;&#9472;sda4   8:4    0  24.4G  0 part /
&#9500;&#9472;sda5   8:5    0  24.4G  0 part 
&#9500;&#9472;sda6   8:6    0    80M  0 part 
&#9500;&#9472;sda7   8:7    0  24.4G  0 part 
&#9500;&#9472;sda8   8:8    0    80M  0 part 
&#9492;&#9472;sda9   8:9    0  25.4G  0 part 
sdb      8:16   1 465.8G  0 disk 
&#9492;&#9472;sdb1   8:17   1 117.2G  0 part /mnt/Common-Files
sdc      8:32   1   7.5G  0 disk 
&#9492;&#9472;sdc1   8:33   1   7.5G  0 part /run/media/dmn/MyData

```

Your setup you show should be fine. Only you know how much space you expect to use.

---

### Post by andrewsc0 on 2016-11-29
Ok I think that clarifies most of my questions. Thanks to the both of you!

---

