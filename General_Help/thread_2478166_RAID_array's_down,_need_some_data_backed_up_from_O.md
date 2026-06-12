---
title: "RAID array's down, need some data backed up from OS"
date: 2022-08-18
forum: General Help
---

### Post by gimpacause on 2022-08-18
Hi All been running my Server for several years (with som awesome help from this community)  now I face a hardware issue and I am unsure how to proceed

I run a server with the following arrays
Single  SSD OS
2 x 2tb SSD Raid 0
15 x 6tb RAID6
15 x 18tb Raid 6

One of the power supplies that power half of the drives in the 2 15 drive array's has died

I have not powered the server back up since

What I would like to do is get the system running (with networking)  and only have the 

2 x 2TB SSD MOUNT,  so I can get some data off the OS from some software I run

How can I accomplish this and tell Ubuntu not to start or mount the other 2 array's with the 15 drives each,  my reasoning is I can backup what I need,  replace the faulty PSU and I should be back up and running with out too many issues

Should I just unplug all power to the array's and boot get my data,  or should I be telling MDADM to not mount them,  thank you

---

### Post by TheFu on 2022-08-18
Troubleshooting often begins by booting into a "Try Ubuntu" environment from a flash drive, then commenting out the things that you don't want to happen automatically.

Of course, you could unplug the array connections too, but that won't stop the system from looking for the disks and arrays. I think you want to avoid that until all the hardware is back working.

I've never used RAID6 or RAID0. Cannot help with those.

---

