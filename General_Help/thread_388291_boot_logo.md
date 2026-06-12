---
title: "boot logo"
date: 2007-03-19
forum: General Help
---

### Post by AAJ on 2007-03-19
Hi,

how i can change the startup system, as we know when ubuntu starting up there is a Ubuntu logo and line for loading. I want to change that like debian linux , opensuse and fedora I mean i want to see what is happen in the background ?

Any idea about that the loading for system look likes xp windows and i want to change it :)

I saw many subject here in this forum to change the logo only but i want to change the way of loading.

Cheers,

---

### Post by guru369 on 2007-03-19
You may want to try adding: splash=verbose to your grub kernel line.

i.e.:
```

kernel /boot/kernel-2.6.20-gentoo-r2 root.... splash=verbose .....

```

Dekel

---

### Post by AAJ on 2007-03-19
where i have to add it in the grub or ???

and did you test it before

Thanks

---

### Post by guru369 on 2007-03-19
When you first see the grub menu type e (the e key on the keyboard)

This will bring you into edit mode. (Dont worry any editing you do here is not saved and the next reboot grub will come back to normal)

Select the kernel line (using the arrows on the keyboard) and type e again. (This will get you to edit mode on the kernel line.

Add to the end of the line splash=verbose and type enter.
then click the b key (on the keyboard) it will boot that kernel.

If you see the boot screen with all the messages you wanted then you can safely add this permanently by editing /boot/grub/grub.conf.

Good Luck
Dekel

---

### Post by AAJ on 2007-03-19
I will try.

Thanks again

---

### Post by cyberdork33 on 2007-03-19
you can also remove spash and quiet from the kernel line altogether and get all the system messages to scroll by in the terminal during startup.

---

### Post by AAJ on 2007-03-19
there is no grub.conf file under grub folder :S

---

### Post by cyberdork33 on 2007-03-19
in ubuntu it is menu.lst

same thing :)

---

### Post by AAJ on 2007-03-19
Resloved , I modifed the menu.list

Thanks all

---

### Post by AAJ on 2007-03-19
lol, in the same time we replied.

in my plan after ubuntu I will install Debian :)

Cheers,

---

### Post by cyberdork33 on 2007-03-19
if you do not edit the automagic kernel list options, then the next time your kernel is updated, it will add those back. make sure you edit the line in your menu.lst file that says:

```
# defoptions=quiet splash
``` how you want all future kernels to show in the list. Don't uncomment the line!

---

### Post by Takagami on 2007-07-29
Turning it off is all fine and dandy but what if I want to change it. I want to create my OWN boot logo and progress bar to show at boot. I'm hoping I wouldn't have to re-compile the kernel to do so. Any thoughts?

---

