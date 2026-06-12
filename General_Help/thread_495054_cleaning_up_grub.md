---
title: "cleaning up grub"
date: 2007-07-07
forum: General Help
---

### Post by guine on 2007-07-07
My grub list has now includes probably close to 10 different options even though I only have one functional operating system on my computer(a breezy install on my first of 2 harddrives).  I also had to manually edit grub a couple months ago to make my breezy install the default boot from my 1st harddrive after edgy died on my 2nd harddrive.  If I install fiesty on my 2nd harddrive will it clean up grub for me and leave me with just fiesty and breezy as my only 2 options(they would be the only operating systems on my harddrives after installing fiesty to replace the dead install of edgy on my 2nd harddrive) with fiesty as the default or would it just add fiesty to my grub list with breezy as the default?  Thanks

---

### Post by Vajra Vrtti on 2007-07-07
If you install Feisty it will create a new grub menu with its 3 entries at the top (normal, safe mode, memtest) and entries to all other kernels it can find in the HDs as *Other Operating Systems* (or something like that) bellow.

---

