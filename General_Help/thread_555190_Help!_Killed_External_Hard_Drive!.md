---
title: "Help! Killed External Hard Drive!"
date: 2007-09-19
forum: General Help
---

### Post by Zeroangel on 2007-09-19
Hey all. I just purchased an External HDD enclosure and put a 10GB drive into it. I then:

- Opened up GParted
- Seen all the old FS allocations (One primary, and one extended with a logical and logical swap partition inside of it)
- Selected the option to write a new disklabel (because I wanted to give the HD a name)
- Exited Gparted, decided to ask around about creating a persistent live install.

Anyways when I reopened Gparted, it said that the drive /dev/sda was empty, there were no allocated spaces.

So I try and set up some partitions but Gparted brings up the create disklabel screen and I tell it 'Yeah, create a disklabel' (since I dont really have a choice). And get a message "Error while setting new disklabel".

Subsequent attempts to use qtparted, fdisk, and cfdisk all fail. They all say that they cannot read from the Hard Disk.

I think I mightve toasted its MBR, or something similar to that. How do I get this hard drive usable again?

---

### Post by Zeroangel on 2007-09-19
Problem solved!

I had more success by doing the following:

- Removing the hard drive from the external case, 
- Jumpering it back to slave, 
- Installing into my PC
- Loading Ubuntu, 
- Then running gparted again and doing all of my partitioning.

It works fine now, and I can still use it externally.

---

