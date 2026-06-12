---
title: "Home partition"
date: 2007-05-16
forum: General Help
---

### Post by atlfalcons866 on 2007-05-16
why should i make a home partition? will programs i install automaticlly go there or do i have to specify where they go like windows. how many gigs should i give the root more and less than the home. i have 160 gb and i am going to allocate 30GBs to ubuntu

---

### Post by J0ris on 2007-05-16
As far as I understand it user-specifc parts of packages that are installed go to the Home directory automatically.
There are a few reasons the /home directory is often assigned a separate partition, e.g.:
- Easier to make a backup of your running ubuntu system
- When for any reason your Ubuntu system needs reinstalling and the partition it's on is therefore formatted all files in your home directory will still be there.
Normally 10GB should be more than sufficient for any Ubuntu system, excluding the home directory.

---

### Post by strabes on 2007-05-16
Put simply, your home folder stores preferences. Therefore many people choose to make a separate home partition so that they can reinstall very easily without backing up much data. Having a separate home partition also allows you to use the same preferences with more than one distribution on your hard drive.

---

### Post by atlfalcons866 on 2007-05-17
does that mean when i install the drivers for my wifi card they will still be there and then i wont have to reinstall it again after a reinstall of ubuntu

---

### Post by dexter on 2007-05-17
> **atlfalcons866 said:**
> does that mean when i install the drivers for my wifi card they will still be there and then i wont have to reinstall it again after a reinstall of ubuntu

Drivers are a part of the core system and are not installed in the home directory. After a reinstall, you will have to install them again.

---

