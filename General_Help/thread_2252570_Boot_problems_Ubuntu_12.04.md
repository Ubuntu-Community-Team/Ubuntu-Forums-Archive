---
title: "Boot problems Ubuntu 12.04"
date: 2014-11-12
forum: General Help
---

### Post by hop5uk on 2014-11-12
I am running Ubuntu 12.04.2 LTS using command line only. My set up is:
1) 2 x 64GB SSD disks configured in Raid 1 and running the Op Sys.
2) 4 x 3000GB disks in Raid 5 for storage
3) 3 x 2000GB disks in Raid 5 for storage
4) 4 x 1500GB disks in Raid 5 for storage
Arrays 1) and 4) are plugged into the motherboard SATA ports.
Arrays 2) and 3) are plugged into the an IBM m1015 controller card.
I am using mdadm for SW control of all arrays.
A few days ago i had a report to tell me that one of the disks in array 2) had failed. This has happened before and my plan was to buy a new disk and follow the same procedure that i did last time and re add it to the array. I powered down the server unplugged the disk and then restarted, just to make sure i had removed the correct disk. It started up OK but to be on the safe side i powered it down again until my new disk arrived.
When it arrived, i plugged it into the vacant power and sata connector but now Ubuntu wont boot. The sequence is as follows:
1. BIOS splash screen ( I am able to go into the Bios if neccessary)
2. Controller card BIOS screen ( I am also able to go into this Bios if neccessary)
3. GNU Grub screen. This gives me the choice of:
[LIST]
[*]    Ubuntu, with Linux 3.2.0-29-generic 
[*]    Ubuntu, with Linux 3.2.0-29-generic (recovery mode) 
[*]    Memory test (memtest86+) 
[*]    Memory test (memtest86+, serial console 115200) 
[/LIST]
At this point i leave the pc to chose the first selection as normal but then the screen just goes blank and nothing else happens.  I wondered if this could just be display but i cannot see the server from any other PC on my network so i know that it is not booting. After doing some reading i decided to try a boot-repair using the installation USB stick. This procedure was unsuccessful but at least it gave me the URL for diagnostics and so please can you take a look at it and give me some guidance.

[http://paste.ubuntu.com/8963156](http://paste.ubuntu.com/8963156)

---

