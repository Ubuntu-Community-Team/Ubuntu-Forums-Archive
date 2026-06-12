---
title: "Best Way To Clone a Drive"
date: 2018-07-02
forum: General Help
---

### Post by spode2 on 2018-07-02
I converted my Windows 7 Desktop to dual boot many years ago by adding an SSD to the machine and installing Lubuntu to it. I rarely boot to W7, but mail, bookmarks and documents are still on the original hard disk and are shared by both OS.

The W7 disk is now starting to show errors, and I want to replace it. Ideally, I would like to install a new drive, clone the old W7 drive to it, and then remove the old drive. Is there a simple and safe way to do this, or should I just use gnome-disks to make an image of the old drive and restore it to the new one? Are there likely to be any boot problems with a new drive i.d. which I should be aware of?

---

### Post by TheFu on 2018-07-02
> **spode2 said:**
> I converted my Windows 7 Desktop to dual boot many years ago by adding an SSD to the machine and installing Lubuntu to it. I rarely boot to W7, but mail, bookmarks and documents are still on the original hard disk and are shared by both OS.

The W7 disk is now starting to show errors, and I want to replace it. Ideally, I would like to install a new drive, clone the old W7 drive to it, and then remove the old drive. Is there a simple and safe way to do this, or should I just use gnome-disks to make an image of the old drive and restore it to the new one? Are there likely to be any boot problems with a new drive i.d. which I should be aware of?

There are 50 different methods. Which is best is highly subjective.  Each method as pros/cons for consideration.
There are at least 20 posts in these forums about this topic.  Disk cloning tools haven't changed in years.

ddrescue is how I'd do it, lacking any other information.

However,  this would be an excellent time to test your backup and recovery processes, when you have less to lose than you've already lost due to a failing disk.   I'd push for you to use those methods for the restore.

If you don't have backups, get some. Soon.  All disks fail and seldom when it is convenient.

---

### Post by HermanAB on 2018-07-03
You can even use the venerable kitty cat to clone a drive:
# cat /dev/sda > /dev/sdb

Contrary to popular belief, it works the same as dd!

---

### Post by spode2 on 2018-07-05
Thanks for the replies, and ddrescue was just what I needed. It even copies the UUID, so no changes needed for the mail files location etc.

---

### Post by TheFu on 2018-07-05
> **spode2 said:**
> Thanks for the replies, and ddrescue was just what I needed. It even copies the UUID, so no changes needed for the mail files location etc.

Glad it worked for you.  Just to be clear, **any** disk imaging tool would accomplish that.  The differentiator for ddrescue is that it keeps going if there are physical errors on either the source or target devices. It tries to get the data, really hard, and only gives up when it is clear the data in that sector cannot be retrieved.

Other imaging tools are smarter about file systems, empty space, compression, and a few other things. If there isn't any trouble reading the source disk, then ddrescue isn't the best tool for most people.   Lots of tools would work and the one that works for you the best/easiest is the correct tool. ;)

---

### Post by spode2 on 2018-07-05
One thing ddrescue did not need to copy is the SMART data. It is a bit annoying not to have a clean slate for the new disk, but I am not about to try every cloning method to find the one which is perfect. I was hoping to find it by asking here :)

---

