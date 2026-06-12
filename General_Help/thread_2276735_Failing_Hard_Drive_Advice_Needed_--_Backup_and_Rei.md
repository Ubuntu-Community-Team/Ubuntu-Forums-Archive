---
title: "Failing Hard Drive Advice Needed -- Backup and Reinstall of Dual Boot System"
date: 2015-05-04
forum: General Help
---

### Post by karat on 2015-05-04
Not sure if this should go in general help of installation, but this isn't a traditional install issue, so I'm opting for general help.

My hard drive is intermittently failing on boot.  That is, it can't be seen on my Lenovo Ideapad laptop for the first 15 minutes it is on, but once it boots, it keeps working.  It's only been like this for a few days, but I think it's only got a few days more left before it dies completely.  I'm trying to figure out what I need to do to rescue my dual-boot Windows/Ubuntu system.  Since this is an Ubuntu forum, I'm going to focus on the Ubuntu questions, but it is relevant that this is a dual boot system.  Here is my plan:

* Purchase a new hard drive and make sure I have a thumb drive and some blank DVDs.
* Copy my homedir onto the thumb drive.  It's only 2 GB, so I'm good there.
** Is there data other than my homedir I should copy?  The only thing I've nontrivially customized are my trackpad settings, so I can also copy the config file for that.  I'm not sure what else.
* Burn an install DVD for the latest ubuntu.  The one I currently have is about 4 years out of date, but it boots at least.
* Uninstall stuff from windows to reduce the space I need and burn a backup onto DVD.  This is because I don't have install disks, just a pre-installed copy (not uncommon nowadays).
* Note the partition information and data useage from both Windows and Ubuntu.
* Swap the drives.  I haven't done this before, but it looks like I could do this in 5 minutes, since the hard drive is easily accessible under the panel.
* Partition the new hard drive.
** Not sure what to use.  Presumably the ubuntu install disk has one?  Can I partition and *not* install (see later on why)? Advice?
** Previously, I had separate logical partitions for boot, system, and user data.  I'm wondering if there is a point to this habit.  Is there an advantage to doing this over just having one drive?
* Use the Windows rescue disk I burned to restore my image of windows.
** I want to install Windows first because grub deals better with Windows than Windows deals with grub.
* Install Ubuntu using the install disk I burned earlier
* Copy my files over from the thumb drive.
* Ignore the Lenovo backup partition.  I'm not sure what it's for and how to transfer it over.

Will that work?  Is there a better way?  Any other advice?

---

### Post by Mark Phelps on 2015-05-04
I discovered only recently that Macrium Reflect (a Windows-based image/backup/restore app) is also able image and restore Linux filesystems!

If I were you, I would do the following:
1) Acquire a new drive as large as (or, preferrably, larger than) your current drive
2) Acquire an adapter to connect the new drive (probably via USB) to your PC
3) Install Macrium Reflect on your Windows system
4) Use the MR option to "clone" your existing drive to the new drive
5) Shutdown your PC and swap drives

If all went well (as it did for me when I did much the same stuff a couple of weeks ago), when you reboot your PC, it will look just like you have it now -- but with a new drive.

---

### Post by karat on 2015-05-05
I need help with step 2. How do I connect an internal drive via USB?  I already bought a drive of the same size. Also, does it work if the drive is not formatted?

---

### Post by SeijiSensei on 2015-05-05
> **karat said:**
> I need help with step 2. How do I connect an internal drive via USB? 
Use one of these: [http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002](http://www.newegg.com/Product/Product.aspx?Item=N82E16812232002)

It's really useful to have one of these if you have a lot of old drives lying around like I do and want to check them out.

---

### Post by karat on 2015-05-05
I got such a connector (Kingston EZ-Connect 2535 -- 2.5 SATA to USB 2.0).  However, windows can't see the drive.  How would I be able to see it in Ubuntu?

---

### Post by Mark Phelps on 2015-05-05
> However, windows can't see the drive. 
HOW are you determining this?  In Windows, go into Disk Management and scroll down through the list of devices.  It should be there in the devices, but will not have a drive letter because it is unformatted.  

However, Macrium Reflect will still allow you to select that as the target drive for cloning.

> How would I be able to see it in Ubuntu? That won't help you with my solution as MR does not run in Ubuntu.

---

### Post by karat on 2015-05-05
I determined it via device manager.  It turns out that one of the connectors was loose and hard to plug in 100%.  Disconnecting and reconnecting fixed it.

The point of asking about Ubuntu was to determine if it was a driver problem or a physical problem -- if Ubuntu could see the drive, it was a Windows-only problem.  If Ubuntu couldn't, then it was a physical problem (which it was).

In the end, it finally worked!  I'm impressed that MR was able to clone the linux partitions correctly.  Thank you.

---

