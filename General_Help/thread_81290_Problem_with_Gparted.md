---
title: "Problem with Gparted"
date: 2005-10-24
forum: General Help
---

### Post by hanspb on 2005-10-24
Hi, I am running Gparted from my Ubuntu 5.10 live-cd, and I have some trouble. My setup is as follows:
Hda (80 GB) containing Windows XP with 3 primary partitions: hda1, small hidden partition, hda2 with NTFS for Windows system (C:\) and hda3 with NTFS for data (D:\).
Hdb (20 GB) containing Ubuntu: hdb1 (extended partition) containing /home, /swap and a fat32 partition, hdb2 (bootable) with the rest. 

Now, since my hdb2 got completely full and won't let me log on any more after the upgrade to Breezy, I want to reorganize things. I want to have my Ubuntu root partition on hda, both to make it bigger and because that drive is faster. So I use Gparted and I try to shrink hda3 to make room for my new Linux partition, but it won't do it! Any ideas why? It is of course not mounted.

---

### Post by Pablo_Escobar on 2005-10-24
I don't think that gparted will do well with NTFS partition (hda3). 
But I don't know it for sure. You can always resize from XP to be on the safe side.

---

### Post by hanspb on 2005-10-24
Well, at least the Gparted homepage says it will resize ntfs, and the option is not greyed out. And to resize from within XP I think I would have to buy Partition Magic or something. I am not interested in that.

---

### Post by saads on 2005-10-24
Make sure you have all of the following installed, that your partition is not mounted, and that you run gparted as root (i think it can only be run as root actually, but just in case):

libntfs5 (REQUIRED)
libparted1.6-12 (should already be installed with gparted)
ntfsprogs (may or may not need this)

---

### Post by hanspb on 2005-10-25
Thanks, but according to the Gparted website, if something that Gparted needs is not installed, then the corresponding activities (such as resize ntfs) will be greyed out in the menu, but it is not. And since I used a live cd i guess it is no use installing anything.
Anyway, it is too late. I simply took backup of my files, deleted the ntfs partition and made a new smaller one from within XP.
So all I have to do now is to reinstall Ubuntu tonight.

---

