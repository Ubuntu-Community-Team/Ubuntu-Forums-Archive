---
title: "Question/Problem with using VirtualBox"
date: 2007-06-10
forum: General Help
---

### Post by wesxohio on 2007-06-10
I'm a newbie when it comes to using Linux and wanted to load Windows above Linux so I could use a few recording programs I am missing oh so much until I play with Ardour & Audacity enough to feel comfortable with recording with it


now.. getting VirtualBox to work.. after installation I went to add a new virtual machine.. I put in my windows xp disk thinking that would do. But it's wanting a .iso file.. how could I either get around this some how or make my xp disk into a .iso file?

thanks a bunch

---

### Post by luisromangz on 2007-06-10
To make an iso from a cd, you can use one of the following commands

dd if=/dev/cdrom of=imagen.iso

cat /dev/cdrom > imagen.iso 

I  hope one of them makes the trick for you!

---

### Post by qpieus on 2007-06-10
Create a new virtual machine and open up the CD/DVD-ROM setting, click on "Mount CD/DVD Drive" and "Host CD/DVD Drive". That should direct virtualbox to use your PC's actual CD/DVD drive. With this setting there is no need to turn your windows cd into an iso. See attached picture.

---

### Post by wesxohio on 2007-06-10
> **qpieus said:**
> Create a new virtual machine and open up the CD/DVD-ROM setting, click on "Mount CD/DVD Drive" and "Host CD/DVD Drive". That should direct virtualbox to use your PC's actual CD/DVD drive. With this setting there is no need to turn your windows cd into an iso. See attached picture.

This Worked!! thanks a lot.

---

### Post by qpieus on 2007-06-10
You' re welcome. Enjoy virtualbox, that's a nice program.

---

### Post by wesxohio on 2007-06-11
> **qpieus said:**
> You' re welcome. Enjoy virtualbox, that's a nice program.

i definetly will at somepoint.. forgot about how dumb xp is with activation.. :(

---

