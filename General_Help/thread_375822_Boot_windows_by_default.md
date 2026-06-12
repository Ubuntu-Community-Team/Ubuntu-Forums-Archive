---
title: "Boot windows by default?"
date: 2007-03-04
forum: General Help
---

### Post by MattVort on 2007-03-04
I have had a look around at various threads, and they all say that if you want to boot Windows by default you have to change loads of values in the grub settings file, and whenever you update your kernel you'll have to change this again. I know the kernel doesnt get updated that often, but this could get annoying.

I know with Fedora you can choose to automatically boot into Windows without having to modify any files - its part of the installation process.

Is it possible to do this kind of thing with Ubuntu? And if so how? If it isnt possible, is it possible to disable the Grub timeout?

---

### Post by darrenm on 2007-03-04
Just edit /boot/grub/menu.lst

Count the number of entries (starting at 0) and change the "default" setting to the number of your Windows entry.

Then run grub-install /dev/hda or /dev/sda depending on your setup. As long as its not inside the automagic kernels list it wont change on updates.

---

### Post by Elena678 on 2007-03-04
Yea, now you tell, i remember, in fedora core you can chouse what you like to set *** default,  mmm, i love fedora core, a bitty it's not working on my laptop, but okei, in ubuntu i never saw this, so i don't know if you can set it that it is the default, the only thing i know is that the grup timout is 10 sec, so when you not go out for a drink or somthing like that, you have lots of time to take the system you like :)

maybe it's not the awnser you was loking for, but i tink somboddy will post it soon :)

greets

edit: oh, i see somboddy allready posted the a better awnser :)

---

### Post by moore.bryan on 2007-03-04
*as far as i know, this isn't possible in ubuntu without editing /boot/grub/menu.lst.  i dumped windows a while ago, so i don't use this, but grub man talks about a "savedefault" switch... look at the beginning of the file.  if one of your switches for windows includes "savedefault" and you set that in menu.lst, then it should automatically go with that one.*

---

### Post by moore.bryan on 2007-03-04
> **darrenm said:**
> Just edit /boot/grub/menu.lst

Count the number of entries (starting at 0) and change the "default" setting to the number of your Windows entry.

Then run grub-install /dev/hda or /dev/sda depending on your setup. As long as its not inside the automagic kernels list it wont change on updates.
*the only downside is when grub-update is run, it'll reorder the choices...*

---

### Post by darrenm on 2007-03-04
But the Windows stanza is put outside of the automagic kernels list by Ubuiqity so unless new entries are added it will always be the same number.

---

### Post by moore.bryan on 2007-03-04
> **darrenm said:**
> But the Windows stanza is put outside of the automagic kernels list by Ubuiqity so unless new entries are added it will always be the same number.
*ubuiqity?  huh?*

---

