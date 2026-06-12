---
title: "Missing file; help with recovery"
date: 2014-09-20
forum: General Help
---

### Post by uvercinka2 on 2014-09-20
Hi,

I have Ubuntu 12.04 LTS with Windows 7 as dual boot. While on Ubuntu, I was using files and folders from the windows partition. I made a folder in the windows partiton, copied in it a ".docx" document from another folder, and edited that file via LibreOffice. I saved and re-edited and saved the document multiple times on ubuntu. But at one point I had to boot to windows, and I saved and closed the document, restarted and booted to windows. I tried to open the folder I made back in Ubuntu, and it gave me an error. So I went back to Ubuntu and now I don't have the folder at all. I tried recovery programs, went back to windows tried over there, also the folder is not there in windows too right now. 

Could anyone help? the document is very important and I have to find a way to recover it. (I also checked if LibreOffice made any copies somewhere but couldnt find anything)

---

### Post by TheFu on 2014-09-21
Sorry, I don't really understand what you did from the description.  
Were you always using the same version of libreoffice or was some other program used? 
Was the filename used 100% compatible between Windows and Linux?  The file systems do not support all the same characters.

Does Win7 have "fast boot?"  [http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/) warns against that.
[http://www.tuxera.com/community/ntfs-3g-faq/#locale3](http://www.tuxera.com/community/ntfs-3g-faq/#locale3) has more on missing files/directories.
In my experience, if libreoffice crashes, the next time I run it, it prompts me to recover the corrupted file.  I've never tried editing the same exact file stored on NTFS from both Linux and Windows. That just isn't the way I work.  File locking with the NTFS from Linux isn't everything is should be, sadly.

So - do you have automatic, daily, backups?
If not, perhaps today is a good day to start?  [http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/) is really, really, easy to understand.

Sorry that I have more questions than answers ... these are meant to help you find the root issue.

---

