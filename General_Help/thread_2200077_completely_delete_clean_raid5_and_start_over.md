---
title: "completely delete clean raid5 and start over"
date: 2014-01-17
forum: General Help
---

### Post by ninjadisco on 2014-01-17
My setup:

Version - Ubuntu 12.04.3 LTS w/ 
Mdadm - v3.2.5 - 18th May 2012
MotherB - Gigabyte GA-Z68MA-D2H-B3
Kernel & CPU -  3.8.0-35-generic on x86_64
Intel (R) Core (TM) i3-2100 CPU @ 3.10GHZ, 4 cores
16GB DDR3 1333 Ram (2 x 8gb sticks)
RocketRAID 2720SGL Host Adapter (6gb/s x 8 channel pci-e 2.0) 
5 X WD RED NAS Hard Drives (3TB 64MB Cache Sata 6.0gb/s - WD39EFRX)
Supermicro SuperChassis CSE-743T-665B Rackmount Server

Not one to normally post asking for help...I'm incredibly stubborn and like to find my own answers but I'm stumped and the amount of time involved with trial and error when it involves rebuilding 15tb's worth of drives has lead me here asking for yours. Please be kind and lend it if you think you can help...would be great to get some insight

I used a web based control (webmin v1.670) to create a raid5 with mdadm v3.2.5 containing 4, 3tb segate barracuda drives. The drives originated inside some cheap external backups which gutted and took the internal 3.5 drives out of to use to hold large blu ray movie rips. The first build with mdadm via webmin took about 2 days for the 4 drives. This was my first time working with raid so I had no expectations time wise. Everything seemed to go ok, but afterwards, every time I rebooted, the raid would be degraded and I'd have to manually reassemble. My lovely wife got me the 5 WD Red NAS drives for Xmas, so I slowly started dropping one of the seagates when it was up and clean, and then readding the WD until I got to the point where 4 were in. I then grew the raid5 with a 5th, and it seriously took 11 days to complete (hovered between 1100k and 5000/k) I tried all the tweaking but came to find out that the 4K sector size applied by webmin was the issue. My read benchmarks were maxing out at 110mb/s and averaging 23mb/s (bottoming . Never have been able to figure out how to do write benchmarks on an active array (I'll post that separateley though). After the 11 day wait to make sure I didnt lose data, I backed up to other externals, and deicded to start from scratch using mdadm in terminal like I should have in the beginning. I stopped the array "sudo mdadm --stop /dev/md0" unmounted "sudo umount /dev/md0" (can't remember which I did first) and then zeroed out the superblocks on the drives "sudo mdadm --zero-superblock /dev/sdf (and the same for sdg, sdh, sdi, sdj)" I then rebooted, and recreated the array with a 256 chunk size (majority of files are >1gb so I went with 256 after some reading online that higher values are better for bigger files) "sudo mdadm --create --verbose /dev/md0 --level=5 --chunk=256 --raid-devices=5 /dev/sdf /dev/sdg /dev/sdg /dev/sdh /dev/sdi /dev/sdj" and it started building. Only took 6 hours so I think the chunk size was likely to blame before.

Ok, so here's where I run into the issue at hand. The folder that was assigned to the previous (now deleted) raid, is still showing in my file manager. "raid5_3tb" is still there under file system, but nothng is in it. It shows 47.4 GB free for some reason. How do I delete this folder? Also, using disc utility to create a file system on the new raid 5, I either keep getting errors that it can't create any paritions, or when it does, they are misaligned by more than 200,000 and I can't mount the volume afterwards.

I'm up for starting all over again, but I need to know what to do to 1st) remove all hisotry of the first, and now second raid5,s from my system (both were /dev/md0) and 2nd) Prepare the drives so they are aligned properly after the raid is built and ready to be partitioned and mounted.

My apologies for the length of this but figured it would be better to be more precise so you have more details. Let me know if you I missed anything you need to know.

Thank you so much in advance!

---

