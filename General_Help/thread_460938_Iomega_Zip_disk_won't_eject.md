---
title: "Iomega Zip disk won't eject"
date: 2007-06-01
forum: General Help
---

### Post by alfreddo on 2007-06-01
Hi,

I have successfully got my PC running Ubuntu v.6.06LTS  Dapper Drake to recognise my 250Mb internal ATAPI Iomega Zip drive - using instructions found here: [http://doc.gwos.org/index.php/IomegaZip](http://doc.gwos.org/index.php/IomegaZip)

The Zip drive is identified as 'zip0'

However, I can't get the zip disk to eject. I've tried the methods suggested on the web page, typing in a Terminal window, with these results:

alfred@Aopen:~$ umount /media/zip0

Didn't work. So then I tried:

alfred@Aopen:~$ umount -1 /media/zip0

And got this response:

umount: invalid option -- 1
Usage: umount [-hV]
       umount -a [-f] [-r] [-n] [-v] [-t vfstypes] [-O opts]
       umount [-f] [-r] [-n] [-v] special | node...

Then tried this: 

alfred@Aopen:~$ eject zip0
not an sg device, or old sg driver
eject: unable to eject, last error: Invalid argument

Then this: 

alfred@Aopen:~$ eject /media/zip0
not an sg device, or old sg driver
eject: unable to eject, last error: Invalid argument

Any suggestions?

Thanks

Alfreddo

---

### Post by alfreddo on 2007-06-02
I've found a way of getting the Zip disk out of the machine.

I unmount the Zip drive using the Terminal umount command. then I reboot. At the point where Ubuntu has closed down but not yet restarted I press the 'eject'; button and the disk is ejected. Clunky but effective.

---

### Post by mltom on 2008-03-08
The link oni how  to install Iomega Zip drive sure does not load on my pc.
Is there another site?

tks
tom

---

