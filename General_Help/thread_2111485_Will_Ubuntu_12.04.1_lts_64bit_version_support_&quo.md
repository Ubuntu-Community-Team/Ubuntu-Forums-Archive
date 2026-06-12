---
title: "Will Ubuntu 12.04.1 lts 64bit version support &quot;Super-speed boot&quot;?"
date: 2013-02-02
forum: General Help
---

### Post by jomoyomo on 2013-02-02
Will ubuntu 12.04.1 64 bit version support super-speed boot in BIOS?
It works like a charm on Windows8, but it will work in ubuntu? if not, How can I use that?

---

### Post by coldraven on 2013-02-02
Just use suspend, problem solved :)

---

### Post by oldfred on 2013-02-02
Windows 8 is not doing anything special. It just is using hibernation. 

And if you have a UltraBook then it also uses a small SSD to cache Windows info.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by jomoyomo on 2013-02-03
> **oldfred said:**
> Windows 8 is not doing anything special. It just is using hibernation. 
 
And if you have a UltraBook then it also uses a small SSD to cache Windows info.
 
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
 
 
 
Thanks for the answer.
If I seperate SSD Volume to two for "/"(Ubuntu System),  and mount "/home" to HDD(partitioned), it won't conflicted by hibernation?

---

### Post by oldfred on 2013-02-03
That has advantages but hibernation is still an issue as that is Windows and Windows expects to be the only operating system. 

Even with hibernation or fast boot turned off in Windows, it still is suggested to not write into the Windows system partition, and set it as read-only if mounted. Then create a separate NTFS shared data partition for any data you may want to use in both systems.

---

