---
title: "reconnecting new install with /home PARTITION"
date: 2007-10-22
forum: General Help
---

### Post by t2000kw on 2007-10-22
I've had some problems upgrading to Gutsy. When I tried to upgrade it trashed my / folder. When I reinstalled Feisty, allowed it to run the 125 security updates on it, that also trashed the / folder and rendered it unbootable.

This time I'm installing Feisty, NOT allow the security updates to take place, download Gutsy, burn a CD if I can (had problems recently so it may be a bad CD-R/DVD+/-R drive but I have a backup drive), then upgrade to Gutsy. 

Once I upgrade, how do I get it to point to my /home PARTITION (it's separate from the Feisty or Gutsy new installation and has all of my saved documents, etc., in it)?

I can find information on MOVING /home to a /home partition but not fixing a new installation  so that it uses my existing /home PARTITION. This is not just a folder in the / partition. It is a separate partiton. I just want to make that clear so that I don't get advice on how to move it to a partition by copying the files over. 

It's probably a matter of doing some of the stuff mentioned in some forum posts, but I don't want to make the mistake of deleting or doing something I shouldn't.

Thanks in advance. 

I will post this in the upgrading and installing forum but this also seemed like an appropriate one since a person reinstalling a version might need to address this item.

---

### Post by p_quarles on 2007-10-22
During the partitioning phase, you should select the "manual" option. This will bring up a list of partitions, listing their device names. Now, all you have to do is specify a mount point for them (Gparted will not automatically detect your old mount points, in other words). The root partition should be assigned "/" and formatted. The home partition should be assigned "/home", and should *not *be formatted. 

Anyway, that's how you do it, so if this sounds a lot like what you already did, I would wonder if perhaps you corrupted the home partition somehow. You should be able to check this by running the live CD and mounting the partitions, then looking at what's on them.

---

### Post by t2000kw on 2007-10-22
Yes, the /home partition got corrupted somehow in the process, though I did tell it to NOT format it. 

Is there an undelete utility to fix this somehow?

It's not a major disaster, but it wold be nice to have some of my documents back.

Don

---

