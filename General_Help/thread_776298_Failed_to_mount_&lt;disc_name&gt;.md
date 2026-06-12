---
title: "Failed to mount &lt;disc name&gt;"
date: 2008-04-30
forum: General Help
---

### Post by riokerr on 2008-04-30
Hi,

I keep on having this reoccurring problem in a new install of 8.04.  After I accessed the floppy drive once (I know who uses those these days LOL), it began putting this annoying message every time I place a CD/DVD in my computers drive.

It usually mounts the disc just fine but places the annoying message:

"Failed to mount <disc name>.

mount block device /dev/scd0 is a write protected, mounting read only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount according to mtab, /dev/scd0 is already mounted on /media/cdrom0."

Any ideas on how to get rid of this irritating problem?  I am trying to set this computer up for one of my parents and I think they will get really annoyed with the error message.  Any suggestions I would gladly appreciate!

Thank you in advance!  

PS.  I have not edited any text files or anything, it just decided to act up like this after using the floppy drive.

---

### Post by mali2297 on 2008-04-30
My guess is that you didn't cleanly unmount the floppy when you removed it. 

Open a terminal and type 
```

umount -fl /dev/scd0 

```
If it complains about permissions, put a sudo in front,
```

sudo umount -fl /dev/scd0 

```

The lesson here is to unmount a device before physically removing it. If you right-click on the appropriate icon, I think you will see an option to unmount or eject.

---

### Post by riokerr on 2008-04-30
Thanks for your suggestion Martin!  I tried <sudo umount -fl /dev/scd0> with something in the CD/DVD drive and in the floppy drive <sudo umount -fl /dev/fd0>.  However, now the floppy will only read after a reboot and then I can't load it again.  The CD continues to display the error "Failed to mount <disc name>. :(

I have never had so many problems with such a new install, I am having problems on my machine too!

Any ideas/ suggestions helpful!

---

### Post by mali2297 on 2008-05-01
Have you used the floppy drive with previous versions of Xubuntu without any problems? It might be a bug that should be reported to Launchpad.

To troubleshoot, try
```

sudo mount -v /dev/fd0 /mnt

```
with a floppy disc inserted. Any errors?

Also, post the contents of /etc/fstab.

---

