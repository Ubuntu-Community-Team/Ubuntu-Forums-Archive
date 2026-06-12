---
title: "[SOLVED] Backup of installed packages"
date: 2008-06-25
forum: General Help
---

### Post by Nxion on 2008-06-25
I'm curious to know. Is there a way it backup all the installed applications on my machine? I ask this encase I need to reload my system or maybe move to another one.

Thanks!!!

---

### Post by geo909 on 2008-06-25
Some people use different partitions on the disk for the */home* and other folders like /etc..
 This way you can reinstall your system without losing any settings.

Of course you can sometimes backup the actual folder that holds the settings for a particular program. For example, firefox holds all the data to a <somepath>/.mozilla/firefox folder and you can back it up by just cp.

 What I do is using clonezilla often for backing up an image of my internal disk. This way I can restore my disk to a previous point if something bad happens.

---

### Post by Nxion on 2008-06-25
> **geo909 said:**
> Some people use different partitions on the disk for the */home* and other folders like /etc..
 This way you can reinstall your system without losing any settings.

Of course you can sometimes backup the actual folder that holds the settings for a particular program. For example, firefox holds all the data to a <somepath>/.mozilla/firefox folder and you can back it up by just cp.

 What I do is using clonezilla often for backing up an image of my internal disk. This way I can restore my disk to a previous point if something bad happens.

Thanks Geo for your quick reply. That sounds nice. Is clonezilla in the repo's?

---

### Post by dexter.deepak on 2008-06-25
remastersys is another good tool to make an exact image of your current install..you can either create a distributable version of your desktop.

---

### Post by Nxion on 2008-06-25
> **dexter.deepak said:**
> remastersys is another good tool to make an exact image of your current install..you can either create a distributable version of your desktop.

Ive heard of that one, Ill give that one as well.

---

### Post by drs305 on 2008-06-25
> **Nxion said:**
> I'm curious to know. Is there a way it backup all the installed applications on my machine? I ask this encase I need to reload my system or maybe move to another one.

Thanks!!!

For installing the same programs over again or making sure the same packages are installed on a new machine, there are commands to save and restore the *list* of packages. It doesn't save the configuration files or save the downloads, it only saves the list. The packages still have to be downloaded again and settings reconfigured. 

But if you would like to simply save a list of the installed packages:

To Save the list (in this example to a file on the Desktop called installed-packages):
```
sudo dpkg --get-selections >~/installed-packages

```

To Restore:
```

sudo apt-get update
sudo dpkg --clear-selections
sudo dpkg --set-selections <~/installed-packages 	
sudo apt-get -u dselect-upgrade

```

---

### Post by geo909 on 2008-06-25
Actually Clonezilla is different from what you asked (though it does the job).

 Clonezilla is a live CD. Try "clonezilla live" on google. It's fast and reliable. You use the live cd to make images of your disks and save them to an external disk for example. So when you rm -rf your root folder or do anything stupid, you just pop in the clonezilla live cd and you bring your disk to the exact situation it was when you backed it up. It's like bringing your disk back in time, to talk in plain words.

 The good thing with clonezilla is that it makes very small images even for huge disks: no matter the filesystem, it does not "count" free space and you can also apply different levels of compression.
 That is, if you have a 500GB hard disk where 50 Gb are occupied, you have an image of 50GBs. If you have chosen a compression the image may be several times smaller.
 
 I love clonezilla and it have saved me two times from disaster. I recommend you should try it if you want a good way to back up your system..

---

### Post by Nxion on 2008-09-30
Thanks everyone :) It worked like a charm.

---

