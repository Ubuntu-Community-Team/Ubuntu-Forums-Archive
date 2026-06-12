---
title: "how to make larger fs based on some partitioned disks? based on files distr on disks"
date: 2020-10-05
forum: General Help
---

### Post by alex346 on 2020-10-05
hello,

I know that is bad approach, but I would need it only for testing purposes.

I have few of raid0 mdadm devices partitioned and occupied in 50%. So I am wasting lot of TBytes as each md device has 2x6TB WD RED drive.

name  total free
md1 - 12tb  6tb
md2 - 24tb  4tb
md0 - 8tb   2tb
md3   24tb 20tb

I would need to get about 20TB based distributed on theses disks, so I would like to make any stripping solution based on files which will be putted on existing parrtitions, putted wth files on the filesystem (ext4).

So I am looking for something which allow me to put on mdadm filesystems:
md1 - 6tb
md2 - 4tb
md0 - 2tb
md3 - 20tb
files which I would like to mount to large temporary filesystem which will sum up to 6+4+2+20 tb. Is that possible?
No, I can;t make these filesystems again, and currently I can;t ythink about ZFS or making it better.
I know that could not be persistent. That is my lab computer which works 24/7.

regards

---

### Post by TheFu on 2020-10-05
ZFS doesn't support reducing file systems.  It does support increasing them easily.

LVM does support reducing file systems AND it supports increasing them easily. Reducing is a pain, but possible. 

LVM supports RAID and striping with only a tiny performance hit compared to straight mdadm RAID, if any.

Regardless of what you choose, I'd create a VM with tiny disks which mirror the full sized setup, just 10000x smaller storage, and try out the stuff you want to achieve.  Instead of 6TB, use 6MB, for example.

My brain just isn't working this morning.  I'd get a few sheets of paper out and start by drawing the system you have today on pg1.  
On page 100, draw the final setup you want.
On the remaining pages, draw how each step will help you migrate from pg1 --> pg100. You probably only need 2-4 pages to get the steps on paper.

BTW, the information above doesn't provide anywhere near the details needed to help. RAID devices are tied to storage. If the storage devices are shared between different RAID devices (say there are 2 - 4 partitions on some), then freeing up storage doesn't necessarily mean freeing up the entire storage device.

In general, when storage is tight, you'll want to start with the smallest devices for the first steps, unless you can borrow/steal/buy new storage for the largest. Having storage for the largest device really would make life easier.  Sometimes, there isn't any way to get from pg1 --> pg100 without buying lots of extra storage.  At least today, we can get 10TB for $200.  I've found USB3 8TB HDDs for $125 multiple times, though I'd never, never, never, ever, use them in RAID. RAID needs eSATA, SATA, or Infiniband connections, never USB.

If you can't make new file systems, then you are stuck. Sorry.  As a cheat, you may be able to use symbolic links to trick programs looking for data on md0 to really find those on md1.  That would free up all of md0, for example.  With that free, you could create LVM+RAID on those devices, allocate LVs of 2TB and 6TB, them move everything off md1 over. 

Now you have 12TB free that was md1.  Create LVM+RAID on those devices, allocate LVs for 4TB and move the stuff from md2 over.  
Now, md2 is empty, so you ahve 24TB to work with there.  Create LVM+RAID on those devices, allocate LVs for 20tb of md3 stuff and move that over.  Seems like this could work, assuming all the md-devices are on different storage, nothing shared between them.  Plus, you end up with extra space that can be either extended for existing LVs or new LVs can be created.  LVM has lots of kewl storage management capabilities when it comes time to move storage around.  Check out pvmove. VG and LV have similar commands, which is useful depends on what you need.  lvconvert has striping and RAID options, but you'll want to understand how PVs, VGs and LVs relate before going that way.  These ARE Unix tools, so if you, the admin, ask to do something stupid, the system will.  That's a way to achieve total data loss.  

I asked LVM to do something stupid about 20 yrs ago.  I said to extend a single file system across 3 partitions on 3 different HDDs. It was great, until one of those disks failed.  I lost all the data on all 3 disks. This event taught me about Backup Religion. I've had it since about that time, though it took until 2008 before I really got the religion.  The only data loss that I've had since then was stuff that was created today, before the nightly backups ran.  With backup religion, your problem wouldn't be much of a problem.  All that storage would have backups, so you could pave everything, start fresh with a better solution that wasn't stuck using fixed partitions sizes like mdadm is. After laying out the new storage, a restore and Bob's your uncle. There are 1001 problems that backups solve, while RAID only solves 2 issues and often only 1.  HA.

You are showing an excellent example as to why using LVM or ZFS and only allocating the amount of storage necessary for the next 3 months is a "best practice".  We've all been there.

---

### Post by alex346 on 2020-10-15
Hey TheFu, thank you for your detailed answer.

So, I have got a detailed plan for next weeks, rather months :)

I really appreciate your hints, and I also understand, that RAID=!=backup and secure storage. Of course I understand risks.


But, currently I am looking for something temporary - as I need lot of space for downloading lot of materials. There is no special need to keep it securely. If I will loose it, I can download it once more.
d
So, writing my previous post earlier I have thought about something like making big .img file , etcetera which could occupy free space, and after that I would use that in mdadm/LVM devices. So, in a result I would have stripped - for example between md1 and md2 - 6+4tb=10tb in total.

---

