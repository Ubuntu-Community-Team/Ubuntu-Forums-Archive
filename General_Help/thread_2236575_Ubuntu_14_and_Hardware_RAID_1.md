---
title: "Ubuntu 14 and Hardware RAID 1"
date: 2014-07-27
forum: General Help
---

### Post by CrimsonEquinox on 2014-07-27
Hello,

Recently I installed Ubuntu Studio 14 on my system and I am having some trouble with my Hardware RAID 1's.  In windows of course, the OS sees the hardware RAID 1's created by my Asus Sabertooth board as single drives and all is right with the world.  Ubuntu however sees them as seperate drives.  My fear is that if I mount one drive and add or remove data from it then the RAID will fail consistancy and subsiquently fail completely.  I have a lot of data on these mirrors, well over 2tb, so any sort of re-RAID'ing is out of the question due to the risk to the data and the fact that Windows would likely not be able to see a linux RAID 1.

Thanks in advance.

---

### Post by Bucky Ball on 2014-07-27
*Thread moved to **General Help**.*

Although you're using Ubuntu Studio, your problem isn't really about that and you have a better chance of support here. Just wondering how a RAID set up will fare if you are doing resource intensive audio/visual recording or editing. But that is off-topic. :-k

---

### Post by CrimsonEquinox on 2014-07-27
When I get to that point, I'll let you know how it goes. ;)

---

### Post by bab1 on 2014-07-27
> **CrimsonEquinox said:**
> Hello,

Recently I installed Ubuntu Studio 14 on my system and I am having some trouble with my Hardware RAID 1's.  In windows of course, the OS sees the hardware RAID 1's created by my Asus Sabertooth board as single drives and all is right with the world.  Ubuntu however sees them as seperate drives.  My fear is that if I mount one drive and add or remove data from it then the RAID will fail consistancy and subsiquently fail completely.  I have a lot of data on these mirrors, well over 2tb, so any sort of re-RAID'ing is out of the question due to the risk to the data and the fact that Windows would likely not be able to see a linux RAID 1.

Thanks in advance.
Is this machine a dual boot host?  The RAID sounds like it is Windows centric.  The RAID you have is most likely *fakeraid*.  This type of RAID is incompatible with Ubuntu as it still needs a software driver.  Although  [this article]("https://help.ubuntu.com/community/FakeRaidHowto") is a little dated it explains the basics well.

It is unfortunate that you do not have the data backed up.  Before you do anything else*** you should back the data up to a safe location***.  The existing RAID setup is absolutly no substitute for backups.  Once this is done you can configure the disk partitioning as you like.

I'm not a big fan of RAID for what you are doing anyway.  RAID is for "high availability".  This usually means a business where "time down is money lost".  I have LVM2 setup and a solid backup scheme.  I haven't lost any data in the last 10+ years although I have had hardware failures like everyone does from time to time.

---

### Post by oldfred on 2014-07-27
I have also avoided RAID, but mostly for different reasons. It seems to add a level of complexity that for a standard desktop is not required. For servers then it would be essential.

Many think RAID is backup but it is not.
       [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

The standard desktop installer does not have RAID drivers, not sure if just adding them to live installer in live mode uses that when installing.

 Elimination of Alternative installer for 12.10 and no RAID support directly for Desktop.
[http://ubuntuforums.org/showthread.php?t=2049021](http://ubuntuforums.org/showthread.php?t=2049021)

Do not know enough about RAID on whether you need the dmraid or mdadm drivers to enable your RAID.

---

### Post by CrimsonEquinox on 2014-08-08
> **bab1 said:**
> Is this machine a dual boot host?  The RAID sounds like it is Windows centric.  The RAID you have is most likely *fakeraid*.  This type of RAID is incompatible with Ubuntu as it still needs a software driver.  Although  [this article]("https://help.ubuntu.com/community/FakeRaidHowto") is a little dated it explains the basics well.

It is unfortunate that you do not have the data backed up.  Before you do anything else*** you should back the data up to a safe location***.  The existing RAID setup is absolutly no substitute for backups.  Once this is done you can configure the disk partitioning as you like.

I'm not a big fan of RAID for what you are doing anyway.  RAID is for "high availability".  This usually means a business where "time down is money lost".  I have LVM2 setup and a solid backup scheme.  I haven't lost any data in the last 10+ years although I have had hardware failures like everyone does from time to time.

Yes, I am actually tri-booting.  2 Win7 Pro and one Ubu Studio.

My Sys drive is not part of the RAID setup, it is a standalone 500gb SATA mounted in a caddy for ease of replacement.  The four drives I have in two RAID1 arrays are merely for storage.  Too many times I have had a single drive die on me and, backups or not, I have been more or less screwed.  With this Rig I went with twin drives in two RAID 1 configurations so that should one drive check out its counterpart would still be accessible.  As for backups, the majority of the data is not worth copying off to other devices... but by the same token I don't want to spend the months required to recreate it all.

I read the fakeraid article and it makes sense, but for now... I guess I am staying in Windows.

Maybe my next Rig I just buy new everything and set it up as you described then move the data from the old rig to the new one.

---

