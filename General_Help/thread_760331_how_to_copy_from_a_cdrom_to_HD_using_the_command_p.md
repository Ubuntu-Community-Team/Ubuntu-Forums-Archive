---
title: "how to copy from a cdrom to HD using the command prompt"
date: 2008-04-20
forum: General Help
---

### Post by jorik42 on 2008-04-20
hi all; i want to use my command prompt to copy some files from my cdrom drive to my HD (to further transfer to a usb stick).  however, i cant figure out how to cd into my cdrom drive.  cd /mnt/cdrom0 returns "no such file or directory."  so im a little lost...any ideas?

jorik

---

### Post by logos34 on 2008-04-20
try 

/**media**/cdrom0

---

### Post by ibutho on 2008-04-20
Look in /media. There should be a mount point for your cd/dvd device. On my Ubuntu 7.10 server the mount point for the cd/dvd device is /media/cdrom0.

---

### Post by jorik42 on 2008-04-20
awesome; cd /media/cdrom0 worked.  thanks for the tip

---

### Post by Bill Roberts on 2008-05-03
With a ubuntu install CD (that I have installed from) in the drive, I cd /media/cdrom0.  I get to the directory, but there are no files.  What am I doing wrong?

---

### Post by jorik42 on 2008-05-04
you might try the command "sudo ls -a" or "sudo ls -l"  that will list all the hidden files.  also, try it with a different cd, such as a data cd or something of the like.  see if you can see any files on that cd.

---

