---
title: "Recovering Encrypted Drives"
date: 2007-12-10
forum: General Help
---

### Post by brewerth on 2007-12-10
I am installing Ubuntu 7.10 on my work computer and I need to have the entire drive encrypted per my employer. I used the alternate install disk and chose to have the entire drive encrypted at setup. 

In the past, with any operating system, I've always found some solace in the understanding that if the operating system itself became so corrupted that I could no longer boot into it, I could take the hard drive out, hook it up to another computer (or use Knoppix) and get my files off. Is this still possible with an encrypted drive? Assuming I have the password, can I mount it with the LiveCD for example, unlock it and transfer my files off?

Just wondering. Thank you in advance.

---

### Post by vanadium on 2007-12-10
As long as you can install the encryption driver on the new OS and remember the password, it should be possible to to gain access to the encrypted volume.

---

### Post by tact on 2007-12-13
> **brewerth said:**
> I am installing Ubuntu 7.10 on my work computer and I need to have the entire drive encrypted per my employer. I used the alternate install disk and chose to have the entire drive encrypted at setup. 

In the past, with any operating system, I've always found some solace in the understanding that if the operating system itself became so corrupted that I could no longer boot into it, I could take the hard drive out, hook it up to another computer (or use Knoppix) and get my files off. Is this still possible with an encrypted drive? Assuming I have the password, can I mount it with the LiveCD for example, unlock it and transfer my files off?

Just wondering. Thank you in advance.

I just did the ubuntu 7.10 whole drive encryption install for the first time a few days ago myself.  

I have a spare HDD for my laptop and normally use it as a back up drive.  Clone the working drive to the spare using dd and then periodically use grsync to keep it updated.

Have been thinking about whole disk encryption for some time and took the plunge.  

Took the working drive out of the laptop (it becomes the working back up now safely stored) and put the spare drive in the laptop.  Installed 7.10 from scratch using the "guided LVM using whole disk....." option.

Copied all my home folders back from the backup (spare) HDD.   Its working nicely.

For the sake of it I slotted a few CDs in the drive and booted from them and tried to access the encrypted drive.  Of course none were able to access it.  :)

I guess we got a lot of research to do to find how to make a recovery CD that has the software needed to be able to access the encrypted drive.

I guess my option (later when sure its safe) is to clone the encrypted drive (my current "working" drive) across onto the spare HDD, wiping out the old back up.

---

### Post by tact on 2007-12-20
following up....

Just for the heck of it I did a full disk encryption install of Gutsy on a spare HDD. 

I am still running full disk encryption on my everyday machine (laptop) too.  It seems nice and stable (as is to be expected from Gutsy) and I have not noticed anything much in the way of slow down in "practical every day" useage.  (This is a corporate "road warrior" working laptop - so we are not just talking occasional email/browsing here.   Nor are we talking gaming.  I do a lot of heavyweight documents/spreadsheets/presentations and routinely run WinXP and Win2k server in VM's).

I did the install by swapping out my production/work HDD last weekend, replacing it with the spare HDD.   Booted up the Gutsy alternate installer and this time chose to partition using the manual option.

/boot is 200MB and on an unencrypted primary partition.  The rest of the HDD is physical container for encrypted volumes.
/ (root) is 9GB and on a logical partition inside the encrypted container.
/home is 100GB and on a logical partition inside the encrypted container.
/swap is 2.5GB and on a swap partition inside the encrypted container.

After installing I swapped the new fresh install out of my laptop and replaced my production/working HDD.   The freshly installed HDD went into a USB drive enclosure for connection as an external drive.

I cannot (yet) get the fresh installed system to boot while its in the external USB enclosure.  (It boots great when installed in the laptop internal drive bay.) 

Will keep on looking into that.  It would be ideal if can boot as an external drive.  The problem is that unlike a standard install (where GRUB is configured with UUIDs to refer to boot and root partitions) the whole-disk encryption setup uses a drive mapper and absolute paths to refer to boot and root partitions.

On the up side -  when I am booted into my (also whole disk encrypted) working/production HDD installed in the laptop drive bay ....  
1.  when I plug in the external drive immediately the unencrypted /boot partition on the external drive is mounted and an icon placed on my desktop.

2.  A popup window also comes up immediately asking for the passphrase for the external encrypted partition and once entered can access the partitions and mount them etc.

Cool what!?  :)

Still toying with it all....anyone interested in more on the matter?  Drop a note.

---

