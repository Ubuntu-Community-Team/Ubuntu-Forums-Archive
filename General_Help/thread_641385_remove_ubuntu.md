---
title: "remove ubuntu?"
date: 2007-12-15
forum: General Help
---

### Post by newcountry on 2007-12-15
how i can remove ubuntu and install other os?

---

### Post by knutschr on 2007-12-15
What other OS?

---

### Post by newcountry on 2007-12-15
> **knutschr said:**
> What other OS?


xp sp 2

---

### Post by r-mo on 2007-12-15
Backup your files, Grab the OS install cd, boot from it follow the destructions

---

### Post by knutschr on 2007-12-15
MS OS will overwrite GRUB too, so after installation you will have no trace of Ubuntu there.

---

### Post by r-mo on 2007-12-15
Why are you leaving btw?

---

### Post by newcountry on 2007-12-15
i did a backup. I start my pc from dvd and i insert the windows cd, after it is searching for hardware and that all, it do not do the installation of windows.

---

### Post by ugm6hr on 2007-12-15
> **newcountry said:**
> i did a backup. I start my pc from dvd and i insert the windows cd, after it is searching for hardware and that all, it do not do the installation of windows.

Either - this is an issue with XP (and you need to ask Microsoft) - or Windows does not recognise your hard drive ext (Linux format) partitions.

If the latter - you can completely wipe the HD and start fresh with [http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by knutschr on 2007-12-15
r-mo about XP installation:
>  follow the destructions
Funny:)

---

### Post by newcountry on 2007-12-15
> **knutschr said:**
> r-mo about XP installation:

Funny:)

Any other way uninstall ubuntu? 

I am leaving ubuntu because i do not find driver for my modem adsl.

---

### Post by ugm6hr on 2007-12-15
> Any other way uninstall ubuntu? 

Have you seen this?
> **ugm6hr said:**
> If the latter - you can completely wipe the HD and start fresh with [http://www.killdisk.com/](http://www.killdisk.com/)

---

### Post by pPrdrm on 2007-12-15
> **ugm6hr said:**
> Either - this is an issue with XP (and you need to ask Microsoft) - or Windows does not recognise your hard drive ext (Linux format) partitions.

If the latter - you can completely wipe the HD and start fresh with [http://www.killdisk.com/](http://www.killdisk.com/)

Windows should recognise that there are partitions on the drive, they just can't tell what kind if they are anything else but Fat or NTFS. If your Hard Drive is a SATA drive maybe windows can't handle it without the SATA drivers from your Motherboard vendor. If that's the case then you should prepare a floppy disk with the drivers and provide it to windows at the start of installation (I think you must press F6 when asked for extra software).

---

### Post by r-mo on 2007-12-15
> **newcountry said:**
> I am leaving ubuntu because i do not find driver for my modem adsl.

What is the modem's make/model?  If you don't know run lsusb in the terminal and this should tell you what's plugged in to the usb ports.

---

