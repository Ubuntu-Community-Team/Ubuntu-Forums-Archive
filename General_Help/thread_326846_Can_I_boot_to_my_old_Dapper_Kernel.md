---
title: "Can I boot to my old Dapper Kernel ?"
date: 2006-12-28
forum: General Help
---

### Post by derby007 on 2006-12-28
I've upgraded to Edgy from Dapper, and i can still see the Dapper Kernel (2.6.15.23 - initrd.old, vmlinuz.old). Can i boot to this kernel by manipulating the file names/links ?

---

### Post by az on 2006-12-28
> **derby007 said:**
> I've upgraded to Edgy from Dapper, and i can still see the Dapper Kernel (2.6.15.23 - initrd.old, vmlinuz.old). Can i boot to this kernel by manipulating the file names/links ?

You can boot that kernel by chosing it in your grub menu.  Don't change the names.  

You can remove the Edgy kernel if you don't want to use it - just use synaptic.

---

### Post by derby007 on 2006-12-28
Yeah, i tried that option in GRUB, but all i got was a 'blinking cursor', and i'm not cursing here, i mean swearing......oooops.
>> ie. all i ended up with is a blank screen & a cursor (blinking)
Any ideas?

---

### Post by derby007 on 2006-12-29
I suppose i'm really asking: can u choose what Kernel u want to boot into simply by choosing it from the GRUB menu. If u can, then WHY can't I......... help !!

---

### Post by derby007 on 2007-01-05
Anyone out there ???????? surely this is a simple fix?

---

### Post by 3rdalbum on 2007-01-05
You usually can. I've run the Breezy kernel on Dapper before now.

There may be incompatibilities between the old kernel and the new software that comes with Edgy.

Why did you want to run the older kernel?

---

### Post by derby007 on 2007-01-05
For the same reason i ventured into Linux/Ubuntu : curiosity / opertunism / understanding
AND the option was in my GRUB, so its like a RED button, press me.... :twisted:

---

### Post by Ramses de Norre on 2007-01-05
I suspect the changes with upstart and dbus and such to cause incompatibilities, if I remember correctly they were the reason why the backports team couldn't port the edgy kernel to dapper, so probably the same reason prevents the dapper kernel to run an edgy system.

---

### Post by derby007 on 2007-01-05
I dunno.....
When i choose that option in GRUB it starts booting but then gives me a blank screen with a blinking cursor. Is there a log i could look at in /var/logs etc ??
then again, as u point out, maybe its not possible....
or how would i get another kernel to boot from, note: i would have to use a CD, ie. no internet connction to the PC in question.

---

