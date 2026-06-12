---
title: "Is it possible to move installed OS on Raid 5 arry to a new computer?"
date: 2008-05-21
forum: General Help
---

### Post by Fredrik_b on 2008-05-21
If I install Ubuntu to a softwere raid 5 arry using altervative install disc. Can I later move the harddrives to a new computer without to much problem?

---

### Post by fjgaude on 2008-05-21
Well, I've never done such a thing, have an bootable OS on a raid5 array. I'm not sure it can be done.

I boot to a single drive and have all my data on a software mdadm raid5 array, which have taken with me to new CPUs, Intel and AMD, new motherboards, upgrades of the OS, etc., without issue.

---

### Post by mrprefect on 2008-05-21
I agree I don't think you can boot an OS from RAID5, only RAID1 as far as I know.

That being said, you should be able to move the array to a new system since the array is arranged using superblocks that denote where the disk is in the array, you should just be able to do a 

mdadm --assemble /dev/mdx /dev/sda1 /dev/sdb1 /dev/sdc1

you can always just tar the OS and dump it to another disk using a boot CD and then re-create the arrary and dump it back on... theoretically.

---

### Post by Fredrik_b on 2008-05-21
The problem is if you boot to a single drive, you have no redundancy. If the system drive fail the computer is down. Also maby more important. If the sytem drive fail, how easy is it to rebuild the raid 5 array?

Using more then 4 drives (will be using 4*750GB sata drives) is not an soulution for me sins I plan to use a shuttle pc in the fall as my server/nas. In the shuttle I can only have 4 3,5" drives. And even that is 2 more than it was designed for. 

Regarding the instalaltion, from what I have read it seems to be possible to create and install to an raid 5 array during the instalation if you use the alternative disk. [Edit: might have read wrong, perhaps it said raid 1]

My first (and second and third) thught was to use openfiler and boot from a USB pen drive, if the usb drive would have faled I would just swap to a backup pen drive. not 100% upptime but accetable. But that Idé I have given up sins I was not able to compile an torrent client with RSS support on that system.

---

### Post by fjgaude on 2008-05-21
A bootable pen drive is a way, but the boot would be slow.

They is problem with handle a failed computer with software raid5 array. When you re-install the OS on a new drive or a newly formatted drive, all you do is download from the repository the file, mdadm, and then at the command line run:

```
sudo mdadm --assemble --scan
```

That command finds the superblocks of each drive and assembles the array. I have the same 4-drive raid4 array for the last three years through two motherboards, from AMD to Intel CPUs... without raid issue, even throug one drive failure and auto resync.

I cannot see how you can boot from a raid5 array as there is no single drive that has all the info needed to load the OS, and that is required before mdadm in loaded. Check again, and you see that only raid1 can boot.

My philsophy is it is easy to re-instal an OS, not so easy to recover lost data. It's complex enough, this raid stuff, to not have to worry about an OS on it.

Let us know what you decide.

---

### Post by Fredrik_b on 2008-05-21
I found [www.pendrivelinux.com](www.pendrivelinux.com) witch seam to be a good solution, having 2 usb drives cloned will make a failed system drive quick to replace.

I will most likely go with Xbuntu on a memory stick. 

Thanks for the inputs

Edit: when I think of it, really no big use of an backup USB/system drive. Will not have an extra hardrive anyway, if one of those fails I will will ned to send that in for replacement annyway. 100% upptime for an home NAS cost to much. An image of the OS is something I will have offcourse.

---

