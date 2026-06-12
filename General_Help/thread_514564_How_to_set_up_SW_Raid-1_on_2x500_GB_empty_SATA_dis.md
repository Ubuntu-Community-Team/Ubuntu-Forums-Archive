---
title: "How to set up SW Raid-1 on 2x500 GB empty SATA disks? (OS on separate disk..?)"
date: 2007-07-31
forum: General Help
---

### Post by Naitsirk on 2007-07-31
Hallois

I recently bought a new motherboard with raid support that turned out to be only "fakeraid" (dmraid), so I am now trying to figure out how software raid works in linux.

My current setup:
6.5 GB IDE-disk with Ubuntu 7.04 Desktop edition installed
2x500 GB SATAII disks with nothing currently on them.

The plan is to have this machine as a home server for sentral storing of documents, photos, homevideos etc, as well as asterisk, web and mail-server if I can get it working.

I am totally new to ubuntu and linux, so can someone tell me step by step the best way of getting my 2 SATA-disks mounted, partitioned and raided?

I think having the 6.5 GB IDE-disk for the OS is the best solution, and I will make some sort of image/ghost of that when it is all set up in case in crashes on me... Unless you think the OS can also as easily be installed on the RAID-disks and be safe no matter which of my two drives should fail?

So far I've figured out I should use gparted and mdadm to get the job done, or at least those are some of my options, but I have no idea how to actually go about doing this and I can't seem to find a howto guide specific enough. (e.g. OS on separate disk and two other disks emtpy and instructions "from scratch").


So here is to hoping someone can help me along with my linux journey.
Thank you all for any and all constructive replies :D


Cheers!



Added:
For some pointers on where I'm stuck.:confused:
1. How can I see if my SATA-disks have been automatically mounted?
2. Should I first partition and then mount or the other way around? And how can this be done?
3. Should the entire 500GB raid-1 be ext3 partitioned?
4. How do I set up the 2 disks in raid, and should that be done before or after mounting?
5. Is this 3-disk setup the best solution with what I've got, or should I just skip the 6.5 gb IDE-disk and get a software raid-1 set up that can boot (contain the OS) which will also be fail safe and easily rebuildable whichever one of the two SATAs fail? Is this possible? (Will only need ubuntu-booting, no dual OS setup..)

Thanks again! Been searching around for a way to do this the last several days now, so hope someone can get me moving along finally.

---

