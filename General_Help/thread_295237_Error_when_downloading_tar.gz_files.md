---
title: "Error when downloading tar.gz files"
date: 2006-11-07
forum: General Help
---

### Post by strabes on 2006-11-07
Whenever I try to download some sort of tar.gz file, it appears where I downloaded it as 0 bytes. This only happens with tar.gz files. Everything else downloads fine. Here is the error:

gzip: /media/data/downloads/.fr.20061.0.res.tar.gz: Operation not permitted
gzip: /media/data/downloads/.fr.20061.0.res.tar.gz: Operation not permitted

Here is my fstab: 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda3
UUID=b461a9b8-6d84-4ddf-aaa7-1cd23b86996a  /              ext3         defaults,errors=remount-ro  0  1  
# /dev/sda4
UUID=d3929551-e00e-47cd-b078-1d7afc28b396  /home          ext3         defaults                    0  2  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto                 0  0  
/dev/sda2                                  /media/data    vfat         iocharset=utf8,umask=000    0  0  
/dev/sda1                                  /media/sda1    ntfs         defaults                    0  0  
/dev/sda3                                  /media/sda3    ext3         defaults                    0  0  
/dev/sda4                                  /media/sda4    ext3         defaults                    0  0  

Any ideas?

---

### Post by Sef on 2006-11-07
Are you running Dapper, Edgy, or other?

Are you using Kubuntu, Ubuntu, or other?

---

### Post by strabes on 2006-11-08
on the top right of everyone's posts it says that stuff. over there ----->   ^^^

ubuntu edgy

thanks for your reply :)

---

### Post by taurus on 2006-11-08
Did you download it using firefox, swiftfox, opera, etc. and where did you download it from?

How come the file has a . infront of it?

Try to download it again BUT this time, save it to your own $HOME directory instead of on VFAT...

---

### Post by strabes on 2006-11-09
I downloaded it from art.gnome.org with swiftfox, and when I download it to my home dir it works fine. The problem only occurs with .tar.gz files on /media/data for some reason. This is really frustrating cuz that's where I store all my files....

---

### Post by taurus on 2006-11-09
Maybe because /media/data is a vfat!!!  vfat/fat32 doesn't take filename.tar.gz (two extensions) too well...

---

### Post by strabes on 2006-11-09
crap. Is there a way around this besides saving it to my home directory?

---

### Post by strabes on 2006-11-18
bump. I know it used to work because I used to be able to save .tar.gz files on that drive easily. something has changed to cause it to stop working.

---

### Post by Ramses de Norre on 2006-11-18
Substitute .tar.gz by .tgz, maybe it works then.

---

### Post by strabes on 2006-11-18
no that doesn't work. It has to be a problem with compressed files. .zip works though

---

