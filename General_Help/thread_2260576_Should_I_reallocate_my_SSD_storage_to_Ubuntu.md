---
title: "Should I reallocate my SSD storage to Ubuntu?"
date: 2015-01-13
forum: General Help
---

### Post by Andrew_Paulus on 2015-01-13
I have a Dell XPS with 750GB HDD + 32GB SSD.

As of right now, Ubuntu is only allocated 25GB of HDD and I was wondering if I could somehow move the Ubuntu OS to the SSD storage and move more of my laptops HDD to Ubuntu for just general storage.

If that wouldn't be worth it, how do I allocate more GB of my HDD to Ubuntu? I want to move about 100GB from my Windows partition to Ubuntu 14.10 so I can have extra space for movies, games, etc..

Thanks! ;)

---

### Post by Bucky Ball on 2015-01-13
Yes. Muchly improved speed on the SSD. I did what you're intending to do when I bought an SSD and I used [Clonezilla]("http://clonezilla.org/"). Here's some links you might find useful:

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

The first link might be what you're looking for. Basically, you clone an image of your install then clone that image to a partition on the SSD (or you can clone directly to the SSD I imagine, but I prefer to go the long way!). So you need to partition the SSD. The partition you clone to needs to be the same size or bigger than the one you originally clone from (and same when creating the original clone).

Clonezilla also allows you to create an ISO of your install which you can then presumably install to the SSD in the normal way, but never used that option.

Good luck. SSD for OSs, HDD for storage. General rule of thumb. ;)

---

### Post by Andrew_Paulus on 2015-01-13
Are there any videos for this? I am nervous and rather watch someone do it step-by-step.

---

### Post by mastablasta on 2015-01-13
It might then be easier for you to 
- move any data to windows side of HDD,
- delete Ubuntu part of HDD & change HDD space to as much as you plan to use
- reinstall the OS on SSD and restore settings from backup (e.g. mint backup tool should do that nicely), and when installing select manual install option. create data partition on your HDD and mount it as /data, create /swap on HDD, create / on ssd. alternatively create / on ssd , create /swap on hdd, create /home on HDD

that should all take about an hour so grab some pizza or something. it should be fairly safe providing you prepare the free (unformatted) disk space you plan to use in advance using windows disk manager. then you just play around in that unformatted disk space. make sure that when creating disk partition you always select unformatted disk space.

---

### Post by oldfred on 2015-01-14
Probably an UltraBook. And they use Intel SRT to  use 32GB drive as cache, and often not all of it but just the same amount as RAM.
Some just install Ubuntu to SSD, Some with larger SSD like yours, leave the cache and use the unallocated for / (root). You only need 20 or 25GB for / anyway, so it may fit.

You may also have issues with the Intel SRT. It used to leave RAID data on SSD which interfered with install. But now it does seem to work if you turn off SRT in UEFI/BIOS and change to AHCI.

        Intel Smart Response Technology
[http://mjg59.dreamwidth.org/26022.html](http://mjg59.dreamwidth.org/26022.html)

 [http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
[http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology](http://software.intel.com/en-us/articles/what-is-intel-rapid-start-technology)

      
 [http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly](http://askubuntu.com/questions/395743/how-to-install-ubuntu-on-xps-15-platinum-2014-version-properly)

Using newer version should be same or easier. 13.10 is now obsolete.
Dell XPS 8700 with Intel SRT -  Install 13.10 - just change UEFI to AHCI mode
[http://ubuntuforums.org/showthread.php?t=2199382](http://ubuntuforums.org/showthread.php?t=2199382)

---

