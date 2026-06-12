---
title: "How to Create a Twin or Even a Triplet of an Ubuntu Installation"
date: 2015-02-28
forum: General Help
---

### Post by oldefoxx on 2015-02-28
Here is an oddball idea.  Suppose you have divided your hard drive into multiple partitions, or actuall have multiole drives (possibly a usb drive).  You are happy with your install of Ubuntu on your primary drive (or you want Ubuntu to go on any other primaryor secondary drive), and it is not enough just to copy it over:  You want it to adapt to its conversion by considering where it is being relocated to , partition type and size, all applications that would be effected by the relocation, even grub.

How would you do it so that is is either a series of given steps, or is there an application yo do it automatically?

The need to reinstall Ubunyu and all application, configure and update them, and user accounts and data yourself would be both time consuming and aggrevating, plus you are likely to miss samwthing somewhere along the way.

---

### Post by tgalati4 on 2015-03-01
Full OS migration is something that is done with virtual machines, but moving to different hardware presents some challenges.  I've used the cp command to simply copy devices and then fix the UUID in grub and /etc/fstab.  Make sure the partitions are the same size.  If larger, then fix with gparted.

Otherwise, some options:  [http://askubuntu.com/questions/452022/remastersys-alternative](http://askubuntu.com/questions/452022/remastersys-alternative)

---

### Post by oldfred on 2015-03-01
I find an install and update to take about an hour. And you just need to copy /home for all your user settings and export a list of installed apps and reinstall those. I have that process as my normal backup, so after hard drive fails I can do that recovery.
It also then does a major houseclean as you do not copy over all that cruft like log files, old kernels, and histories that do build up. Of course if regularly housecleaning like you should that is not an issue.

As tgalati4 says, you can copy with cp  or rsync and update settings. There also are a few other hidden settings that should be updated. If good with command line & mounting partitions from live installer so you can edit those files it can be done. But does not save a lot of time.

---

### Post by tgalati4 on 2015-03-02
I had to create 10 instances of an installation for an embedded linux project.  I simply used:

```
sudo cp /dev/sda /dev/sdb
```

swapping the drive (sdb)  after each copy.  Then I went to each machine and changed the grub UUID entry so that it matched the drive that was installed.  And then changed the /etc/fstab entry so that the correct UUID was mounted.  This required booting a LiveUSB and making the configuration file changes.  I could have used remastersys to respin the distro into an installer and then load that on each, or I could have done a network install or I could have created virtual machines and copied images to each.  There are several ways to do it.

---

