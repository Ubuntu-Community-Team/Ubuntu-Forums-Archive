---
title: "File Size Exceeded"
date: 2008-06-22
forum: General Help
---

### Post by William_in_Kanata on 2008-06-22
I need to move/copy an 18Gb file from my Kubuntu system to a directory on a Windows XP machine. The file currently resides in the /tmp directory on my Kubuntu machine. The directory into which I wish to copy it is mounted on the kubuntu machine via an smbmount with 777 permissions. Either as a regular user, or root (via sudo -i) the copy/move will fail with the message "File Size Exceeded" at 2Gb. ulimit (as either a regular user or root) returns "unlimited". I have not been able to find anything on the Windows XP machine that limits the size of files. Anyone run accross this before and have a work around?

TIA

---

### Post by editrix on 2008-06-23
Your file is bigger than my entire hard drive, so this is just a guess, but ...

[http://www.cyberciti.biz/faq/file-size-limit-exceeded-error-under-linux-and-solution/](http://www.cyberciti.biz/faq/file-size-limit-exceeded-error-under-linux-and-solution/)

BTW, I found this search Google Linux (see my sig).

---

### Post by mcduck on 2008-06-23
Is it a FAT partition? FAT can't handle files larger than 2GB..

---

### Post by geirha on 2008-06-23
Are you using samba? [http://ubuntuforums.org/showthread.php?t=347711](http://ubuntuforums.org/showthread.php?t=347711)

---

