---
title: "access ext HD from Windows"
date: 2013-06-22
forum: General Help
---

### Post by cmcanulty on 2013-06-22
I have a 2TB ext hard drive for backups. If I partition it to 1TB ext4 and 1TB ntfs will windows be able to access the ntfs partition? Or will the partition  that is ext4 cause it to not be used from windows?

---

### Post by dino99 on 2013-06-22
you can indedd read/write to/from linux/windows
[http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/](http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/)

---

### Post by cmcanulty on 2013-06-22
I know windows can read the ntfs what I am unsure of is can windows read an external hard drive that is 1/2 ntfs and 1/2 ext4, thanks

---

### Post by cmcanulty on 2013-06-22
I should clarify, I want to be able to read the ntfs part from any windows without installing any app. I use many computers at our library and don't want to install anything on those machines (all the public machines I have Ubuntu on) but I can't convince the staff to leave windows (yet!)

---

### Post by cool110 on 2013-06-22
Windows will only try to access the 1st partition of removable USB drives.

---

### Post by oldfred on 2013-06-22
Should not normally be an issue.

Things that have caused issues may be hibernation where a file in that partition is still open.

Also in Linux you can use characters that are invalid in Windows.
If an internal drive we would mount with windows_names. I am not sure what the default mount from Nautilus or other file manager may be.

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
For ntfs UUID shown is example only see below:
UUID=DA9056C19056A3B3 /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

If not a permanent mount just do not use those characters in file names. 
I sometimes have had issues backing up files to my DVD with either very long paths or very long names like some of the music or other downloads have done. This was not a just a Linux issue but something in the ISO DVD standards.

---

### Post by cmcanulty on 2013-06-22
OK thanks all my ntfs is the first partition on the ext HD so should be OK

---

