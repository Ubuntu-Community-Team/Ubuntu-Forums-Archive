---
title: "system hangs during startup"
date: 2006-12-29
forum: General Help
---

### Post by glendavee on 2006-12-29
On startup (Edgy) the startup screen appears, then when the scroll bar is about half way, screen switches to the file check screen, with file swap, root file and file systems all showing ok - note, there is no file check going on. System sits there with a blinking cursor for approx 80 secs, and then startup resumes. I've tried installing Bonager and using this to force a scan, same result.
Contents of /etc/fstab are :
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sdb1
UUID=d32be766-a3a3-4717-bab6-b2a123b2e9ec  /              ext3         defaults,errors=remount-ro  0  1  

/dev/hda                                   /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sda2                                  /media/sda2    ntfs         nls=iso8859-1,umask=000,ro  0  0  
/dev/sdc1                                  /media/sdc1    vfat         defaults                    0  0  
/dev/sdb1                                  /media/sdb1    ext3         defaults                    0  0  
/dev/sdb5                                  none    swap         sw                    0  0  
/dev/sda1                                  /media/sda1    vfat         defaults                    0  0  
/dev/sda2                                  /media/sda2    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    vfat         defaults                    0  0  


Any suggestions out there as to how to stop this?

---

