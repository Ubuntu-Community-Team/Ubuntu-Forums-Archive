---
title: "Harddrive failing - steps to migrate to new one"
date: 2021-07-08
forum: General Help
---

### Post by yaminb on 2021-07-08
HI all,

A have a harddrive that is giving me bad sectors and is probably on the verge of failing. Can anyone help outline the plan to have it replaced?

Here's the setup.

sda = 2 TB seagate.  failing drive
   sda1 = 490 GB old ubuntu install. I don't really need this one, but I have it.
   sda2 = 32 GB swap
   sda3 = 1.5 TB home (this is shared between sda and sdc)
   sda4 = 10 GB fat EFI boot partition
   

sdb= 2 TB seagate with windows installed. Shouldn't need to touch this one
sdc = 500 GB SSD
   sdc1 = 1 GB fat EFI boot partition
   sdc2 = 499 GB ubuntu install

Yes, I know I have a lot of wasted space with the EFI partitions :)
Yes, I know I don't need multiple ubuntu installs. I just like the freedom of knowing if something mucks up on one drive, I have another one I can quickly just boot into.


My plan:
1. Purchase a 2 TB ssd drive to replace sda

What would you recommend I do to replace sda with the new SSD?

Is there a clone utility as the drives are the same size? Is this method reliable?
Or would you recommend me just setting up the new SSD with a fresh partition/install and then copying the /home over manually?

Once that is copied though, I assume I'd need to change my sdc Ubuntu install to point to that new /home?
Would I also need to 'refresh' GRUB to handle change of drive, or would this be transparent?

Thanks,

---

### Post by oldfred on 2021-07-08
I always suggest new install, others may suggest clonezilla.
Do new install & restore from your backup. This also confirms your backup includes everything you need to restore system as sometime drives just crash without warning and a restore from backup then is only option. At minimum you need /home, and list of installed apps. You may edit some system files in /etc. I copy the few I change into /home for backup. 

New install also does major housecleaning of old log files & other cruft that builds up over time.
And allows changing partitions around.

If using multiple installs, often better to have /home inside / (root) and have a large data partition with all the data normally in /home. Then you can have different settings in /home but mount data & have same data. I have multiple installs, so I can test changes without corrupting main working install. And I like to install each new release, but keep current LTS as main working install. Every install then has same data, but no conflicts with settings in /home.

---

### Post by yaminb on 2021-07-08
Thanks Fred,

I think i will do that.

How does this plan sound:

1. connect the new SSD via a USB enclosure. 
2. Partition and install Ubuntu on it.
3. Copy the current sda /home to the home partition on the USB enclosed SSD.

[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
This seems useful for changing which is a mount point of /home. I'd have to 

4. Turn off PC, unplug sda. Plug in new SSD into sata for sda.

---

### Post by rsteinmetz70112 on 2021-07-08
I tend to use ddrescue on failing drives. It can create an image and clone the drive exactly. It can retry weak sectors and sometime recover the data. The only problem is that the new drive must be exactly the same size or larger. even a little smaller won't work.

---

### Post by yaminb on 2021-07-08
Right now the drive still appears fully readable/working. It just has 1 bad sector and I'm seeing some stalls as it reads from the disk. I don't think there's been any data loss right now. But the HD looks to be going bad.

---

### Post by scorp123 on 2021-07-08
Just copy away /home onto an external disk ... you don't really need the rest. Install a fresh OS onto a new SSD and then carefully restore your old contents from your old /home into your new one.

---

### Post by Autodave on 2021-07-08
Whenever I suspect a HD is failing, the very first thing that I do is to copy anything and everything that I might need from that drive.

---

### Post by dragonfly41 on 2021-07-08
You already have one point of failure. Your failing hard drive.
As a general rule I try to at least duplicate my drives (n+1 rule) so that if one goes I have at least another (setting aside backup devices).
So instead of a single 2TB SSD, I purchased two 1TB SSD's to place in a Startech dual docking bay with its own power supply.
Each SSD is also placed in an SSD container so that it can be plugged into the dual docking bay (as can your SATA drive).
You can install SSD's internally in the host PC,  but this external docking bay is more convenient. The only point to watch is to use USB 3.0 port for additional performance.
Windows 10 still sits in the old internal hard drive. 
I have read recently that future Windows 11 insists that secure boot is always on in bios whereas with dual boot so far it can be switched off. But Windows 11 is still some time away.

---

### Post by TheFu on 2021-07-08
+1 for ddrescue if the source HDD is failing and you have 24 hrs to let it copy.  The source and target HDDs need to have the same size sectors (512b or 4Kb) and the target needs to be at least the same number of sectors or more.

If not, backup the stuff you want to keep and do a fresh install onto the new storage, then restore the stuff from your backup.  Ideally, that backup should already exist from last night.  Lots of threads here say what is important to backup and the technique to capture the list of installed applications so those are easy to add back in.

---

### Post by yaminb on 2021-07-08
My data is pretty well backup now. I sync most documents using OneDrive and have a NAS locally.

I just like to have everything going. I *could* pretty easily wipe and reinstall everything. But I like to have my computer always ready to go because it is so crucial for my work and most of my life.

---

### Post by TheFu on 2021-07-08
A fresh install is 15 minutes.  Restoring settings and previously installed programs is another 15 minutes.  Important data, 5-15 minutes. Junk data ... takes however long it takes.

Basically, it is 45 minutes to "your system", just refreshed.

A new install also means your restore and be placed onto completely new hardware and prior storage mistakes can be easily corrected.  Just a though.

---

### Post by Unguidedone on 2021-07-09
copy the data to an external drive
do a clean os reinstall
allow the setup scripts to partition so you dont waste a lot of space
ssds are cheap now so just get a 4tb ssd and regular hdds for mass storage

---

### Post by TheFu on 2021-07-10
A 4TB SSD is NOT cheap.  You must live in a completely different world from most people.
I'd be hard-pressed to say that a 500G SSD is cheap or that a 4TB HDD is cheap.

It all depends on the budget of the person involved.

But if you are offering to buy a 4TB SSD for someone, I'd actually prefer to have a 4TB WD-Gold.  Please.

---

