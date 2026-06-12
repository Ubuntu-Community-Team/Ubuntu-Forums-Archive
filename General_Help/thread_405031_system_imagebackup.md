---
title: "system image/backup?"
date: 2007-04-09
forum: General Help
---

### Post by drumkitcat on 2007-04-09
Hi,
I'm running Edgy 6.10 on my Toshiba A40 Satellite Laptop.  Everything works beautifully, but I'd like to be able to make a full system image or backup in the event of a hard drive failure or some other disastrous occurance.

Can anyone recommend a software title to make a disk image that I can write to a cd? or something I can use to back up the operating system?

thanks

---

### Post by Jose Catre-Vandis on 2007-04-09
The current linux way is to use partimage.

The best way to use it is to download a copy of SystemRescueCD, a small linux rescue cd.

On boot, type partimage and follow the instructions. You will need a sepearate partition to save the files.

Plenty of proprietary options: Ghost, Partition Magic, Acronis Disk Director

---

### Post by TheWizzard on 2007-04-09
i backup only /home and /etc

here's a tutorial on making snapshots wit rsync.
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)

dirvish is an interesting backup tool: 
[http://www.dirvish.org/](http://www.dirvish.org/)

---

