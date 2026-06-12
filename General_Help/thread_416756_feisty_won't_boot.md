---
title: "feisty won't boot"
date: 2007-04-21
forum: General Help
---

### Post by ranko on 2007-04-21
hi everybody!

i installed feisty yesterday (clean install, i was running edgy until now). the live cd booted just fine, and the install completed with no problems. however, the first time i tried to boot the new system from the hard drive, it wouldn't boot. this also happened on every subsequent attempt to boot.

anyway, the boot process hangs right at the beginning. after i select ubuntu from the grub menu, it says
"starting up...
loading, please wait..."
in text mode. it then goes into the graphical splash screen, and that's where it hangs, right at the very beginning of the boot process. so the only things that get outputted to the command line are the two lines above. i don't think that even the kernel has been loaded at that point.

i'd like to be able to get some kind of log at this point. something a bit more detailed than the two lines that get outputted to the command line.

does someone have an idea why this is happening or how i can get some additional info on the problem?
as i said, the live cd booted fine and there were no errors during the installation.

thanks!

---

### Post by Arne_M on 2007-04-21
press crtl alt F1 during boot (or in your case at the beginnig) - it should show the console

---

### Post by ranko on 2007-04-21
> **Arne_M said:**
> press crtl alt F1 during boot (or in your case at the beginnig) - it should show the console

thst'a what i did, and there was nothing outputted to the console other than those two lines.

---

### Post by ranko on 2007-04-22
* bump *

i've also tried turning off the "quiet" kernel option in the grub menu, before booting ubuntu. i stil get nothing new in the command line...
i'd like to at least be able to post some more detailed information so maybe someone will have an idea what's going wrong.

---

### Post by glantucan on 2007-04-25
Hello folks
I've got the same problem. After clean install, I can boot my previous widow$ partition and ubuntu in recovery mode. If I try just the default option (ubunto 7.04) It hangs on a blank screen. The keyboard does not respond.
Any clue?

Glantucan

---

### Post by glantucan on 2007-04-25
I found out that deleting the **splash** option from the:
```
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=1f108089-052a-4310-b41f-416685422465 ro quiet [COLOR="Red"]splash[/COLOR]
```
line in menu.list solves the problem for me. I saw this hanging on boot problem in several places in the forum without solution, but I think this is the one. 
Guess the **splash** option doesn't work with certain graphic cards.

To change this you can boot in recovery mode and edit the menu.list with:
```
pico /boot/grub/menu.list
```
It's quite at the bottom of the document.

Or you can select the [COLOR="Sienna"]Ubuntu, kernel 2.6.20-12-generic[/COLOR] at the grub menu and press 'e' to edit manually. You'll be able to boot in graphic mode and then you'll have to   edit menu.list as previosly axplained to make the changes permanent.

EDIT: After reading [http://ubuntuforums.org/showthread.php?p=2264521](http://ubuntuforums.org/showthread.php?p=2264521) I think I better understand what's happening. It seems ubuntu 7.04 boots by deafult with a resolution higher than 1024x768. Probably because most of the people have now flat screens with higher resolution. If I'm right I consider this a big mistake. Anyway, just follow my instructions and, if everything works fine you can try:
 ```
kernel		/boot/vmlinuz-2.6.20-12-generic root=UUID=1f108089-052a-4310-b41f-416685422465 ro quiet [COLOR="SeaGreen"]**splash vga=791**[/COLOR]
```
vga=791 sets the boot resolution to 1024x768. You will have your nice splash screen with the right resolution :D
Regards.
Glantucan

---

