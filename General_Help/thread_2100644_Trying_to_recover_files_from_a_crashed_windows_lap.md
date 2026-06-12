---
title: "Trying to recover files from a crashed windows laptop"
date: 2013-01-02
forum: General Help
---

### Post by Jamzaj on 2013-01-02
Sorry if this topic has already been covered but I searched around and couldn't find anything that helped/made sense to me. I've never used ubuntu so I have no idea what i'm doing (sorry) but heard it could be used to recover files.

So I installed ubuntu onto a USB using another laptop, booted it from my laptop, selected "try ubuntu". 

Now I want to access my files on the hard drive, but when I click on my hard drive it comes up with an error message saying "Unable to mount location. Adding read ACL for uid 999 to ' /media/ubuntu' failed:Operation not supported"] (*,)

Would really appreciate some help from a more knowledgeable person than myself :biggrin:

---

### Post by imachavel on 2013-01-02
ok you see how this works?

danel@danel-Dimension-4700:~$ sudo /bin/bash
[sudo] password for danel: 
root@danel-Dimension-4700:~# ls /media/
apt  floppy  floppy0  iso  Ubuntu 11.10 i386
root@danel-Dimension-4700:~# mkdir /media/disk

These are your basic commands here to mount the hard drive file system(make readable) from a linux live cd. Should work the same from an OS installed to a flash drive:

[http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/](http://www.howtogeek.com/howto/windows-vista/use-ubuntu-live-cd-to-backup-files-from-your-dead-windows-computer/)

My only question is this site, because I'm not sure how you back files up to a live cd. But with a flash drive the answer is obvious you are going to put the files into the flash drive, preferably in a folder ;)

---

### Post by ajgreeny on 2013-01-02
It is possible that the NTFS partitions of your crashed windows OS might need to be force mounted as they may be marked as still in use, not having been shutdown properly by windows.

The link shown by imachavel gives details of that so read it carefully and see if it gets you anywhere.

You may need a separate USB drive to backup all the files you need as you will probably not be able to save files to the USB with ubuntu on it, unless you have set it up with persistence, and that will only be a maximum of 4GB, so if there are lots of files to copy over, get another USB drive for the backup.

---

### Post by Jon Hanna on 2013-04-03
Ubuntu LiveCD/USB tries to mount the drives for the machine off /media/ubuntu, but doesn't come with /media/ubuntu there to use.

Really this is a bug, but it's easily fixed. Either bring up a terminal and [FONT=lucida console]sudo mkdir /media/ubuntu[/FONT] or else [FONT=lucida console]gksu nautilus[/FONT] and create the directory called [FONT=lucida console]ubuntu[/FONT] inside [FONT=lucida sans unicode]/media[/FONT] that way.

After that, it should mount fine.

---

