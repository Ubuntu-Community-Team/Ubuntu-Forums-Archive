---
title: "NIGHTMARE - Dual Boot XP x64 FUBAR + Upgrade to Hardy"
date: 2008-05-31
forum: General Help
---

### Post by YWELLC on 2008-05-31
Currently dual booting XP x64 and Gutsy.  Windows install is now FUBAR.  Unfortunately, some Win apps need to be installed on this box for work (Quickbooks, Office etc.).  I need to preserve the dual boot environment.

I have diligently attempted recovery to no avail.  I believe that a fresh install is inevitable.  On a positive note, I want to use the occasion to upgrade from Gutsy to Hardy.  

I purposely partitioned the box to have a separate /home partition and would like to preserve/transfer all the data therein stored (music, documents, etc.) when I wipe everything else clean for the new doze and Hardy install.  I have no problem re-acquiring the other software (COMPIZ, GnuPG, other easily attainable packages) currently installed.  I am only a novice Linux user and would appreciate any assistance to this end. 

Further, it was a nightmare to install Gutsy on this box, dual booting with  XP x64.  I have an out of the box Dell Dimension E510, including a wireless mouse/keyboard which was incompatible with every Ubuntu install method other than UNetbootin.  As well as non-friendly physical location (and wireless setup) which eventually required a WGA600N to wireless G/N "Gaming Adapter" bridge to connect to my Linksys router in another room, and a slew of other problems.  I thought this time it would be a good idea to ask for some advice from the pros before I go at it alone.  Any help would be greatly appreciated.

---

### Post by logos34 on 2008-05-31
> **YWELLC said:**
> Currently dual booting XP x64 and Gutsy.  Windows install is now FUBAR.  Unfortunately, some Win apps need to be installed on this box for work (Quickbooks, Office etc.).  I need to preserve the dual boot environment.

Have you tried running these apps on Wine in linux?  (you've probably already checked--just thought I'd ask).  Or maybe Crossover Office (but it cost$).  

> I have diligently attempted recovery to no avail.  I believe that a fresh install is inevitable.  On a positive note, I want to use the occasion to upgrade from Gutsy to Hardy.  

Feel free to describe the problem in more detail.  But you seem to have already resigned yourself to a reinstall/upgrade
> 
I purposely partitioned the box to have a separate /home partition and would like to preserve/transfer all the data therein stored (music, documents, etc.) when I wipe everything else clean for the new doze and Hardy install.  I have no problem re-acquiring the other software (COMPIZ, GnuPG, other easily attainable packages) currently installed.  I am only a novice Linux user and would appreciate any assistance to this end. 


> 
[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
#

Identify your current '/' (root) partition. Select '/' as the mount point and ensure that Format is ticked. You will lose all data on this partition and the new version of Ubuntu will be installed there instead.
#

Identify your swap partition and set its mount point as 'swap'.
#

**Identify your /home partition. Set its mount point as '/home' and make sure that Format is [COLOR="Red"]not[/COLOR] ticked**.


Too bad you had such a hard time.  I had pretty much the same dualboot setup as you and never had any issues of note. Wired and wireless worked no prob both side, no booting problems, incompatable peripherals, only little annoyances from time to time. Guess I was just lucky with my hardware.  But now windows is gone for good, and good riddance because, fortunately, I've found perfectly suitable substitutes/workarounds for everything

---

### Post by nanog on 2008-07-06
BootitNG shareware can fix many mbr and partition corruption issues. It will also resize an NTFS position in seconds as opposed to the hrs(ntfs-3g).

PS: I no longer used windows but I do use NTFS drives.

---

