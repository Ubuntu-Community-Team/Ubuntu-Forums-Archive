---
title: "Root folder full - cannot seem to win this"
date: 2015-05-13
forum: General Help
---

### Post by MorneDJ on 2015-05-13
Hi All,

First, I have followed the steps on:
[http://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full](http://askubuntu.com/questions/266825/what-do-i-do-when-my-root-filesystem-is-full)
[http://askubuntu.com/questions/147956/why-is-the-root-partition-on-my-disk-full](http://askubuntu.com/questions/147956/why-is-the-root-partition-on-my-disk-full)
[http://askubuntu.com/questions/57994/root-drive-is-running-out-of-disk-space-how-can-i-free-up-space](http://askubuntu.com/questions/57994/root-drive-is-running-out-of-disk-space-how-can-i-free-up-space)
and a few others. I have been experiencing this problem for the past week but after trying everything I have found no joy.

**_Background (no need to read this but it might provide the necessary background how I got here)_**

First, I do not know Ubuntu well, and have managed to get by by using Google and resources such as can be found here. Thanks all. We a small company with 10 employees. 

Now: I use Ubuntu 10.04.2 server, running on a HP Microserver N40L with 8 GB ram. The server is used as a file server using Samba, nothing else. I run the server from a 8 GB flashdisk. I setup webmin with no graphical interface. It does not even have a screen. I have it setup so that there minimal writing to the flashdisk to save diskspace. 
```

tmpfs                  /var/log    tmpfs     defaults    0    0tmpfs                  /tmp            tmpfs     defaults    0    0
tmpfs                  /var/tmp    tmpfs     defaults    0    0
```

There is a few other changes in fstab and grub to prevent crap being logged. I never setup SMART monitoring tools, neither did I setup any mail and stuff, thinking that I will monitor the server. That was 2 years ago and the server has worked perfectly for that period (yes, Ubuntu is amazing). It ran in software RAID 5, using 4 disks, a spare and 3 active disks. Some-where one of the disks died, and it quietly started using the other, and, having no address to tell me, kept quiet. Then a second disk failed about 2.5 weeks ago, and the morning we got to the office it ran in a degraded state with the server being unworkable slow (at first I thought it was the switch or something else, only after testing all other factors I realized it was the server, confirmed when I went into webmin).

After getting over the shock I did a backup (4 days - 3 TB, valuable documents). After making a backup of that disk (cannot be too careful), I used a second N40L PC I have and installed Ubuntu again, this time version 14.04 (tried 15 but the server appeared very slow). I setup RAID 5 again, but also installed a 5th hard drive to do a rsync every night of documents that was changed during the day. I setup SMART monitoring tools to run weekly tests, as well as mail for various functions.

**The problem (still background but likely the reason of the mess)**

At first I mounted the 5th hard drive manually and setup a cron job for rsync. I manually started a rsync and over 2 days did a full backup. I then activated the rsync cron job. I however made a small mistake in pointing it to the wrong directory (root folder, about 90 folders). A complete mess of incorrect locations and the 3 TB drive is full. It sends me 500 emails one night telling me that. 

Instead of deleting anything I selected to remove that drive, add a new 2 TB drive, manually mounted it and rsync about 1.1 TB of the important documents. I however forget to edit the 5th (backup) hard drive details in fstab. That night I restarted the server, and much later rsync started to finish the job. Naturally the Backup hard disk was no-where and it send me about 1,000 emails telling me that. At the same time one of the hard drives failed ... new !!!!!! So mdadm is emailing me that it is rebuilding etc and that it is running in a degraded state. No problem, I fixed fstab, restarted and problem solved. Cancelled the rsync cron job and waited for the rebuild to finish. Order new hard drive (will exchange warrentee drive later). All seems fine ...

Week later I start webmin as server is very slow. Gives error that it cannot write to some config file, disk full. Opening Disk and Network Filesystems shows the / (Root filesystem) as being 100& full.

Turning to Mr. Google I got a few pages with tips, help etc. Easy I thought, and followed everything. And, after 3 days I have not managed to regain a few bits. While it does not slow the server down it for some reason uses all the virtual memory when it runs the rsync cron job, with the server slow like hell the following morning, requiring a restart (which takes an hour after I gave the shutdown command). So I got a 16 GB flash drive and after some experimentation cloned my 8 GB drive and my root folder is now almost double in size. Restart, no change.

So, back to webmin and I see that I resized the wrong folder. So, after quietly crying in the corner I am writing this email. Problem is that people work on the server during the day, so all this need to be done at night, and I also only have this much time. Please help me diagnose this problem. While I can reinstall the server (likely the fastest option) I would prefer to sort this out and learn something at the same time.

(tonight I again will resize the folder, making a 8 GB root folder - have a new 32 gb drive and I am not afraid to use it).

---

### Post by TheFu on 2015-05-13
Didn't read any of the background.

For non-power users, google solutions for Linux aren't always a good idea.

Support for 10.04 ended last month.  You need to upgrade.  Sadly, forum policy limits our ability to help.

I would perform a fresh install (14.04 LTS) onto a larger HDD and size the partitions to be larger using the "do something else" option" at installation for all the storage. Migrating almost everything from 1 system to another isn't that hard ... if you have the background. 

If you can boot into Ubuntu on the current machine, please post the output from these commands (please, please, please use "code tags" so things line up  -Adv Reply):
```
df -h
df -i
sudo fdisk -l
sudo vgdisplay
sudo lvdisplay

``` That's an example. Note the "code" above the block.

We can get a feel for what storage you are truly working with from those commands.  These facts remove mis-interpretation chances. Thanks.

**Unasked for Advice**
If you are going to be the Unix admin for a company, google can be extremely dangerous to your systems.  Making a commitment to learn Linux in a directed way will save hours, days, weeks, months of frustration. For example, an *out of storage* is an easy issue to resolved by using extra storage, softlinks, and file/directory permissions, why you work though cleaning up some space.  Explaining that is non-trivial to someone without the appropriate background, however.  As long as the files are moved to a different partition, but "appear" to be in the same location with the correct permissions on the limited space partition, life will be good (mostly).
Get that background: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux)  when you get some time.   Skills build on other skills which build on other skills. Cannot jump to 3rd level without having L1 and L2 completed.

---

