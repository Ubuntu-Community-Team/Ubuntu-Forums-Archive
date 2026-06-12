---
title: "Partition error - tried most solutions, none work"
date: 2016-03-01
forum: General Help
---

### Post by jeremy68 on 2016-03-01
Hey, all. I'd like to thank you in advance for reading this, even if you  cannot offer appropriate assistance. Unfortunately I have no  screenshots due to the trouble I'm experiencing.

I recently  decided to install Xubuntu as a dual-boot option on my HDD. After  attempting to partition the remaining free space on it (a free space  ~900gb) from the Xubuntu installer, the installer returned error code  141 after trying to create the 1st ext4 partition (Not sure if this is  relevant but I created three: Two primary partitions and a swap space.  After trying to boot back into Windows so I could research this error,  the message "Reboot and select proper boot device" appeared and it  seemed, at the time, as if Windows was not going to boot. I had  attributed this to a hypothetical terminal problem with the HDD; for  some time before this I was hearing clicks and various other noises  coming from the HDD. I purchased a new WD Blue 1 terabyte and installed  it.

I ran the Xubuntu installer once again, and received the same  error in terms of the creation of the partition. I decided to run  Xubuntu from the thumbdrive and possibly use gparted to  sort the issue out (with the new HDD) and I see the entire hard drive  was unassigned; the exclamation point denoting a warning was also  showing. The error, according to gparted, was that the disk label was  unrecognized. Trying to create a new partition table, the gparted  informed that there was residual GPT data on the hard disk; I knew this  was impossible being that the drive was new but nevertheless I ran gdisk  to erase any gpt data "present" on the hard disk. Thinking the problem  was solved, I ran gparted again and . . . found the same error. Same  problem with the warning symbol (unrecognized disk label), and the  attempt to create a partition table shows that the ghost gpt data still  exists. If I ignore both of these and try to create partitions anyway,  none of the partitions are created; the error given is "unrecognized  disk label". I can attempt to create the label myself using mklabel  following various instructions online but to no avail. 

I seem to have tried everything; it must be something I am doing, no? I appreciate any help given.

---

### Post by lisati on 2016-03-01
Duplicate of [http://ubuntuforums.org/showthread.php?t=2315718](http://ubuntuforums.org/showthread.php?t=2315718) closed

---

