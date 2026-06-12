---
title: "How do I quit live CD?"
date: 2005-07-08
forum: General Help
---

### Post by sillyboy on 2005-07-08
Super NuBee

I was poking around on the live CD, and decided to quit.  How do you do this?  I tried to eject the Live CD, but Ubuntu did not recognize my CDRW (Asus).  I had to hit the reset button then go back into the bios to make the 1st boot device the floppy.  I then could open the CDRW with the button.  The CDRW button would not open at all when the Live CD was running.

Any ideas??

Thanks    O:)

---

### Post by tszanon on 2005-07-09
When you insert a CD, you have to mount it before you can use it. Before ejecting it, you have to unmount it. It can be done automatically, but I don't know how.

To mount a CD, try this:
```
sudo mount /dev/cdrom /media/cdrom0
```
It will ask for your password. The actual directory may be a little different, like just '/media/cdrom'.

To unmount a CD, try this:
```
sudo umount /dev/cdrom
```
It may ask for your password again. The '/dev/cdrom' must be the same you used when mounting.

If it doesn't help, please come back and tell us it didn't work. :-)

---

### Post by z_pod on 2005-07-11
[QUOTE=sillyboy]Super NuBee

I was poking around on the live CD, and decided to quit.  How do you do this?  I tried to eject the Live CD, but Ubuntu did not recognize my CDRW (Asus).  I had to hit the reset button then go back into the bios to make the 1st boot device the floppy.  I then could open the CDRW with the button.  The CDRW button would not open at all when the Live CD was running.

Any ideas??

Thanks    O:)[/QUOTE]
 Hi,

live-cd will eject automatically as you shutdown or reboot your computer (by using "logoff -> restart" menu or by entering "sudo shutdown (reboot)" from a terminal window).

Regards

---

