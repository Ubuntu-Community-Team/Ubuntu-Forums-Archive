---
title: "Ububtu Power Off Issue"
date: 2008-02-21
forum: General Help
---

### Post by JPFX on 2008-02-21
Hi,
I have recently installed Ubuntu 7.10 Desktop Edition on a PC with a AUSTek A7S333 Motherboard and am having shut down power off issues. When I shut down the PC it doesn't power off. I have read about ACPI and APM but am unsure what my motherboard uses and how to resolve this.
Any help?

Cheers,
Daniel.

---

### Post by angrboda on 2008-02-21
hi there,

I suspect your board does have acpi implemented but the bios dates  pre - 2000 (or else is known to have problems with acpi?). Since Some older acpi implementations cause problems acpi defaults to off with boards that report a bios date < 2000 (I think it was 2000). Try to add an
```
acpi=force
```
option to your your kernel options in /boot/grub/menu.lst. If bios age is the problem, that should fix it.
If you want to be careful copy the entry for your standard kernel and  add the option to that. That way you will still have your old setup as backup should anything funny happen...

---

### Post by JPFX on 2008-02-21
I added acpi=off to the /boot/grub/menu.lst like this:

kernal /boot/vmlinuz-2.6.22-14-generic root=UUID=009a3684-4fba-40f7-a21f-ae32988d481f ro quiet splash acpi=force

This still didnt work, this is my first lunix install so any help would be much appriated.

---

### Post by corbcox on 2008-02-21
I had the same issue and I resolved it after finding somewhere on the forums to add this to the line as in the previous post:

  acpi=force pci=noacpi   

  Hope this helps.

---

### Post by JPFX on 2008-02-21
I added the line above and now when I reboot in gets stuck at "Starting Up" how do i fix this?

---

### Post by corbcox on 2008-02-21
Your system may be doing a disk check.  Every 35 boots or so it will do that and will take quite a while to bootup all the way.  Be patient and let it sit for awhile to see if  the system finally comes up.  Could take 2-5 minutes.

---

### Post by JPFX on 2008-02-21
Just managed to get it going again after removing these lines  using grub edit on start-up now boots is this any help?

---

### Post by corbcox on 2008-02-22
Sorry I'm can be of no help.  Hang in there though.  Use the search option in the forums and you will come across the "fix".  Perhaps before you find it someone will post an answer here  that will help you. 

It is a great community here and I know you will enjoy learning  Ubuntu once you get the initial issues out of the way.

---

### Post by confused57 on 2008-02-22
See if anything here will help:
[http://ubuntuforums.org/showthread.php?t=699506](http://ubuntuforums.org/showthread.php?t=699506)

---

### Post by angrboda on 2008-02-22
hi again...

The acpi=force option does exactly what one would think it does: it forces the use of acpi for power management... even if the kernel does not like it. As older implementations were somewhat bug-ridden/unstable they are not used by default. Forcing the use does always mean risking instability. It is very likely that your board does either not support acpi at all, that its acpi support is buggy _or_ simply turned off in your bios settings (did you check?).
If it is not a notebook we are talking about that should not be a problem, however, since most features that you need for a desktop system are available via apm. (follow the link(s) posted above to learn more about that).
btw: The pci=noacpi option afaik does not do very much more than exclude the pci subsystem from acpi. This is needed in some older hardware (with a buggy pci bios?) like my rather aged notebook, for example to prevent hang-ups on the drives...
If acpi is enabled in the bios settings and the "force" option leads to problems, my advice would be use apm instead... To avoid conflict it might even be a good idea to turn acpi support off in the bios should you opt for apm: In my experience the two systems do not like each other too well ;-)

---

### Post by angrboda on 2008-02-22
I just remembered something that might just be worth adding: I had some trouble with the acpi functions on my notebook recently. That stopped when I updated to the latest kernel. So in case you still have an older version: try updating to the latest (ubuntu-) kernel...

---

### Post by JPFX on 2008-02-24
I added apm power_off=1 to the /etc/modules and apm=on to the /boot/grub/menu.lst but still didnt work, i also tried adding acpi=force after this but this didnt work either. Cant find anywhere in the bios that lets you change ACPI or APM for this board.

---

### Post by plucky on 2008-02-24
JPFX,

Have you tried it with ```
acpi=off apm=on
``` in the kernel line of **menu.lst**. 

This will get Ubuntu to turn off ACPI and use APM instead.The default for Ubuntu is ACPI, so if you use ACPI=force the Ubuntu will use ACPI.


Good luck

---

### Post by confused57 on 2008-02-24
> **JPFX said:**
> I added apm power_off=1 to the /etc/modules and apm=on to the /boot/grub/menu.lst but still didnt work, i also tried adding acpi=force after this but this didnt work either. Cant find anywhere in the bios that lets you change ACPI or APM for this board.
See the suggestion in reply #4:
[http://www.linuxquestions.org/questions/ubuntu-63/shutdown-doesnt-but-does-give-halt-error-622114/](http://www.linuxquestions.org/questions/ubuntu-63/shutdown-doesnt-but-does-give-halt-error-622114/)

---

### Post by JPFX on 2008-02-24
> **plucky said:**
> JPFX,

Have you tried it with ```
acpi=off apm=on
``` in the kernel line of **menu.lst**. 

This will get Ubuntu to turn off ACPI and use APM instead.The default for Ubuntu is ACPI, so if you use ACPI=force the Ubuntu will use ACPI.


Good luck

Tried this and it Worked! Thankyou very much.

---

### Post by panda84 on 2008-03-22
Also this thread can be useful:
[http://ubuntuforums.org/showthread.php?t=729450](http://ubuntuforums.org/showthread.php?t=729450)

Bye,
Diego

---

