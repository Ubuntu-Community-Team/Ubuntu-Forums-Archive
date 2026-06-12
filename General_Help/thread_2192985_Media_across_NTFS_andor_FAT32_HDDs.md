---
title: "Media across NTFS and/or FAT32 HDDs?"
date: 2013-12-10
forum: General Help
---

### Post by maxson-chester on 2013-12-10
Hi,

I'm in the process of building a linux media box, but one of my hard drives is NTFS and full of media I'd rather not lose. It's a 2TB, and there will be an additional 3TB that is empty and waiting to be put to use. When googling I've found some different answers as to whether ubuntu will have difficulties reading the media. I am not needing or wanting to boot from this drive, it only contains media. 

Do I need to put my 3TB into my windows machine, format it into FAT32 and then copy all of my media over to it, then format my 2TB to FAT32? If this isn't necessary, how should I format my 3TB?

Thanks for the help!

---

### Post by drmrgd on 2013-12-10
Ubuntu will have no problems reading NTFS.  On the other hand, Windows won't read a linux filesystem.  Plus I think there's a size limit for FAT32 that's way below 3TB.  Have to look that one up.  

I would say format it as NTFS if you just want to use it as a media drive.  That seems the most simple scenario.

---

