---
title: "MBR or LVM partitioning?"
date: 2013-06-11
forum: General Help
---

### Post by ladasky on 2013-06-11
Hello everyone,

I've been asking some _[very specific questions]("http://ubuntuforums.org/showthread.php?t=2153652")_ in the Installation and Upgrades section which haven't been getting any replies.  (Maybe because I provide too much detail?)  Anyway, let me try to ask a short question.  

Suppose you want to create a system which will be able to boot two versions of Ubuntu, one of them being 13.04.  You use RAID1 and mdadm.  You want to share a swap partition and a home partition between the two operating systems.  So, you need four partitions in all, no more.

Do you choose the tried-and-true MBR partitioning system, or LVM partitioning?  Why?

Thank you!

---

### Post by oldfred on 2013-06-12
Your other thread is only 3 hours old. You have to give more time especially for specific questions that are more technical and not used as much. Also since RAID, you may do better in the server sub-forum as they use RAID. 

I do not use RAID and do not particularly like it for desktops. Many users use RAID thinking it is a backup and it is not. It is for reliability, speed and uptime for systems like servers. And those running servers have separate daily, weekly, monthly backup procedures. 

I also do not suggest to share /home although in some cases you may be able to most have it work. But depending on version you may eventually run into conflicts. I prefer to share data partitions with data on multiple drives, not your RAID but manually copied and then most important data archived to DVDs. I prefer manual copy so when I accidentally delete a file it still is in my backup where on your RAID it is gone in both places.

Now SSDs give more speed for a desktop and good backups with rsync or whatever you prefer can give you data reliability. 

But I use gpt for all drives that will never have Windows install, which for me is now all drives. I have not converted older drives that were MBR(msdos).

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

This user likes LVM. Note same user as gpt post above & is the one that created gdisk.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

---

### Post by ladasky on 2013-06-12
> **oldfred said:**
> Your other thread is only 3 hours old. You have to give more time especially for specific questions that are more technical and not used as much.

Thank you very much for your detailed reply, oldfred.

But my _[original thread]("http://ubuntuforums.org/showthread.php?t=2140218")_, referenced in my thread from earlier today, is actually three *weeks* old.  Even though dual-booting is widely used around here, I simply could not install 13.04 side-by-side on my system with 12.04.  I set up a dual-boot Windows/Ubuntu system for my son two years ago, with little difficulty.  I've read many posts here about dual-boot systems, so I didn't think that this would be such an obscure issue.  I am contemplating breaking my 12.04 system, and starting from scratch.  It's going to hurt.  

> **oldfred said:**
> Also since RAID, you may do better in the server sub-forum as they use RAID. 

I do not use RAID and do not particularly like it for desktops. Many users use RAID thinking it is a backup and it is not. It is for reliability, speed and uptime for systems like servers. And those running servers have separate daily, weekly, monthly backup procedures.

Well first of all, I also do manual backups to an external drive, and occasionally also to DVD.

Second, my RAID1 saved me a lot of trouble about a year ago.  I had one of my two hard drives fail (under warranty, thank goodness).  I booted from a live CD, disassembled the RAID, and continued to work.  When the replacement drive arrived, I plugged it in, reassembled the RAID, and let it synchronize.

> **oldfred said:**
> I also do not suggest to share /home although in some cases you may be able to most have it work. But depending on version you may eventually run into conflicts.

What kinds of conflicts do you anticipate?  I don't expect to be running a dual-boot configuration for long, actually.  It's just an insurance policy for a few weeks.  I love Linux and Ubuntu, but I have trouble chasing down build dependencies manually when I get out ahead of the Ubuntu repositories.  I run into this problem repeatedly with a few applications (GROMACS, Python 3, wxPython, and Matplotlib).  It is only those applications that I would need to run from the older OS, while I reconstruct them in the newer OS.  I actually expect to *solve* some of my manual build problems by upgrading to 13.04 -- but I know that I will inevitably break things, too. 

> **oldfred said:**
> I prefer to share data partitions with data on multiple drives, not your RAID but manually copied and then most important data archived to DVDs. I prefer manual copy so when I accidentally delete a file it still is in my backup where on your RAID it is gone in both places.

Point taken.  As I mentioned, I also do manual backups.  I have three copies of my data -- two on my RAID, one on an external drive.

> **oldfred said:**
> Now SSDs give more speed for a desktop and good backups with rsync or whatever you prefer can give you data reliability.

I'll keep that in mind the next time that I have money to spend. :)

> **oldfred said:**
> But I use gpt for all drives that will never have Windows install, which for me is now all drives.

Also true for me.  WelI, actually, I do run Windows in a virtual machine on those rare occasions when I must.  But I keep its filthy paws off my hardware.  :P

> **oldfred said:**
> I have not converted older drives that were MBR(msdos).

       GPT Advantages (older but still valid)  srs5694 post #2:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
GPT or MBR
[http://ubuntuforums.org/showthread.php?t=1625285](http://ubuntuforums.org/showthread.php?t=1625285)

This user likes LVM. Note same user as gpt post above & is the one that created gdisk.
 Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Thank you, now that was VERY helpful.  LVM and GPT solve several problems inherent in MBR.  While most of the problems mentioned aren't _my_ problems, the Ubuntu wiki specifically suggests that LVM may help people who "like to test various Linux distributions."  Even though I don't see my partition count exceeding four, that still describes my situation well.

I'm not quite sure how LVM or GPT interact with RAID.  I'll have to read more to figure that out.

---

