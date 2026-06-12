---
title: "USB external drive not mounting on boot"
date: 2008-02-24
forum: General Help
---

### Post by Welcomed Rain on 2008-02-24
When I first installed Ubuntu (Gutsy is my first Ubuntu version) it would automatically mount my external USB drive on boot (cold plug). I have upgraded to a new computer and installed Vista and Ubuntu Gutsy Gibbon but now my external USB drive (ntfs) will no longer mount automatically when booting. I can mount it using Storage Device Manager (or manually) but its a bit of a pain since the USB is where all my music is (which means every time I boot I must manually mount the USB drive).

Here is the associated line for the external USB drive from my fstab 

"/dev/sdc1     /media/Backup_Disk  ntfs nls=iso8859-1,users,auto,umask=000,user  0  0"

I thought the exclusion of "noauto" or the inclusion of "auto" in the options section would have the drive mount automatically on booting but it does not.

Any help would be appreciated.

---

