---
title: "Wiping Drive Hangs"
date: 2014-05-23
forum: General Help
---

### Post by John_Nosetip on 2014-05-23
I've booted from Live CD(USB) in hopes of completely wiping the drive of a computer I plan to install ubuntu on.  I tried formatting with disk utility and shred -v -f /dev/sda5 but at the current pace it will take two weeks if then.  

A little history...
I tried to install ubuntu on the computer i'm wiping but when I got to the partition section things like new partition table and delete were disabled.  Therefore, I'm trying to wipe the drive via the live cd boot.  FYI according to disk utility the drive is ok but has 2 bad sectors.  

I have no idea what to try next so any help would be greatly appreciated.

---

### Post by plucky on 2014-05-23
> **John_Nosetip said:**
> I've booted from Live CD(USB) in hopes of completely wiping the drive of a computer I plan to install ubuntu on.  I tried formatting with disk utility and shred -v -f /dev/sda5 but at the current pace it will take two weeks if then.  

A little history...
I tried to install ubuntu on the computer i'm wiping but when I got to the partition section things like new partition table and delete were disabled.  Therefore, I'm trying to wipe the drive via the live cd boot.  FYI according to disk utility the drive is ok but has 2 bad sectors.  

I have no idea what to try next so any help would be greatly appreciated.

Have you tried running **Gparted** from the Live CD/USB?

---

### Post by John_Nosetip on 2014-05-23
Thanks for reply.  I have tried but there was some issue.  It was yesterday when I tried it so I can't remember exactly what the issue was.  I kicked off gparted about 10 minutes ago to refresh my memory and it is still scanning for devices.

---

### Post by coffeecat on 2014-05-23
> **John_Nosetip said:**
> shred -v -f /dev/sda5 but at the current pace it will take two weeks if then.

That will only shred the partition sda5, not the partition table, and certainly not the whole disk. The default number of passes for shred with the options you chose is only 3, so if it's going to take 2 weeks, then that must be one very big partition. I can shred a whole 500GB drive - 3 passes - in a few hours. How big is your drive?

However, unless you wish to securely delete everything first, using shred is unnecessary.

> **John_Nosetip said:**
> 
I tried to install ubuntu on the computer i'm wiping but when I got to the partition section things like new partition table and delete were disabled.

Were you trying to use Gparted or Disk Utility from your installed Ubuntu? If so, you won't be able to manipulate partitions that are mounted, and that would include any extended partition if any of the logical partitions are mounted. Ditto the partition table. You certainly won't be able to write a new partition table on the drive from which a running system is running. 

> **John_Nosetip said:**
> Therefore, I'm trying to wipe the drive via the live cd boot.

Use Gparted from the live CD. The live session will probably have mounted the swap partition which will lock it, and will also lock the extended partition if the swap partition is a logical one. In Gparted, right-click on the swap partition and choose "swapoff". 

> **John_Nosetip said:**
> FYI according to disk utility the drive is ok but has 2 bad sectors.  


You say OK. Have you done a full SMART test from Disk Utility?

---

### Post by sudodus on 2014-05-23
I would stop the wiping now.

1. Get ***mkusb*** and wipe the first megabyte. See this link [Ubuntu Forums tutorial "Howto make USB boot drives"]("http://ubuntuforums.org/showthread.php?t=1958073")

2. Use ***gparted***. Select the Device pull-down menu and create a partition table. Then edit partitions.

3. Install your operating system.

---

### Post by John_Nosetip on 2014-05-23
250 GB drive.
I was booting from Live CD when using gparted, disk utility and shred.
I used shred because I didn't have success with gparted or disk utility.  
I'll try running a full test and see what happens. Considering how slow things are running I'm not sure how that will go

---

### Post by sudodus on 2014-05-23
It is important to check the drive. Let us hope it is OK.

There might be some traces from the earlier installation that makes gparted confused, and often it is enough to wipe the first megabyte to remove that problem. It is very fast to wipe 1 MB.

---

### Post by John_Nosetip on 2014-05-23
FYI! fdisk -l doesn't return anything

       lsblk  returns
             sda                                    232.9G
               sda5                                 232.6G
                  ubuntu--vg-root (dm-0)    231.6G   
                  ubuntu--vg-swap (dm-1)   1020M
             
             sdb                                       1.9G
               sdb-1                                  1.9G

             sr0                                        1024M
           
             loop0                                      861M

---

### Post by sotiris2 on 2014-05-23
That's because you need 
```
sudo fdisk -l
```

---

### Post by John_Nosetip on 2014-05-23
thanks! Little embarrassed I missed something so simple

---

### Post by buzzingrobot on 2014-05-23
Unless someone wants to write over/delete/obscure the existing data on a disk, partitioning is all that needs to be done to a drive to install an OS.  No need to format, etc., before installing since the Ubuntu installer formats partitions (unless the user selects "Something Else..." in order to manually partition the drive and opts not to format one or more partitions).

An existing partition scheme can be used or new partitions created.  This can be done in the Ubuntu installer or prior to installation using a partitioning tool like gparted/parted, fdisk, etc.

---

### Post by John_Nosetip on 2014-05-23
Agreed but the install never would start.  Moreover, the functions on the partition editor during install were disabled so there is something in existing partitions that is causing an issue.

---

### Post by John_Nosetip on 2014-05-24
Dell Desktop 
2006 - 2014  RIP

After spending a good part of the day trying different things I still couldn't figure what was wrong with hard drive.  Considering I got 8 good years out of it I decided to mothball it.  Thanks for everyone's help trying to remedy the situation.

---

