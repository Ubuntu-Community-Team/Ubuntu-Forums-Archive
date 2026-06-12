---
title: "RAID Repair after renamed devices"
date: 2008-05-30
forum: General Help
---

### Post by Lord_Devi on 2008-05-30
Hello all.

Rather new to software linux raid, I have encountered my first problem. It seems simple to me on the surface, however I am not sure how to actually go about fixing the problem. To make it short, my RAID 5 array consisted of 3 devices. After popping a new HD into the computer the array is on, some of the devices were renamed(the /dev devices) and the array is no longer assembling properly. I was hoping that simply editing my mdadm.conf to represent these changes would be enough - but I guess I am not that lucky.

The basic layout of my RAID array before the problem:

/dev/md0 consisted of sdb1, sdc1, and sdd1.

After installing a new SATA drive the devices were changed, and I am not exactly sure in what order(I could use fdisk disk id's to determine this by unplugging the new hd and restoring the old setup I suppose if I need the information to reassemble it in order tho). But now I have no more sdd1. Instead one of the array elements is now sda1.

So before:
sdb1, sdc1, sdd1
Now:
sda1, sdb1, sdc1

Essentially I need to tell mdadm where that 3rd device (sdd1) went and to look at sda1 instead. However I hesitate to do anything myself like --remove and --add until I know exactly what is going on and that my data will be safe. 

How do I reassemble this raid, and is there anything important I should keep in mind when fixing this?

---

### Post by fjgaude on 2008-05-30
What I would do is rename or delete the /etc/mdadm/mdadm.conf file and simply then run:

```
sudo mdadm --assemble --scan
```

mdadm doesn't need the .conf file to assemble. It scans the superblocks to determine how the drives are arranged to assemble. It doesn't use the drive names... they can be anything and change all the time. mdadm doesn't care.

---

### Post by Lord_Devi on 2008-05-30
Thanks for the reply.

However that does not work. When I try to use assemble scan, I get
mdadm: /dev/md0 has been started with 2 drives (out of 3). For some reason it will not add the last drive to the array. Any ideas?

---

### Post by fjgaude on 2008-05-31
You did rename or delete the mdadm.config file?

Nothing has changed with the drives superblocks and that is how mdadm assembles arrays, not the drives names.

You do not want to --build or --create as that will destroy your data.

There is no reason to try to --add a drive back, for it is already seen as part of the array. If you have removed the .config file I guess I don't have any further suggestions.

Are there things you have done that you haven't stated? All drives are on the same controller? All are SATA or PATA? What version of Ubuntu are you using?

---

