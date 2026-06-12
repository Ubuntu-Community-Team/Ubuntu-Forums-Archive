---
title: "booting sticks with &quot;[sdb] Asking for cache data failed . . ."
date: 2015-12-14
forum: General Help
---

### Post by Dreamer Fithp Apprentice on 2015-12-14
14.04, 32 bit, with plain Openbox. Worked fine for months but for no reason i can see, the boot process never gets to lightdm. I get through grub normally. I have the logo splash screen turned off. It gets past the part of the boot where the screen goes black for a few seconds. It doesn't really hang - more like some kind of infinite loop. I get 2 lines repeated over and over again, unchanging except for the numeral in []s at the start of each line, I presume a time stamp. Like this:

[56.039547] sd 3:0:0:0 [sdb] Asking for data cache failed
[larger number] sd 3:0:0:0 [sdb] Assuming drive cache write through
[larger number] sd 3:0:0:0 [sdb] Asking for data cache failed
[larger number] sd 3:0:0:0 [sdb] Assuming drive cache write through
[larger number] sd 3:0:0:0 [sdb] Asking for data cache failed
[larger number] sd 3:0:0:0 [sdb] Assuming drive cache write through
. . . (and so on)

On any given boot attempt the "sd 3:0:0:0" remains the same, but randomly on different boots it may be "sd 6:0:0:0" instead.

Everything I've found about this error message suggests it is related to some additional removable media, but I have none in place. No cd in the drive, no thumb drive, no little card, nuthin. I think I had this error once before on a different machine and it was from having a bad cd in the cd drive. I don't have an sdb. This is an old laptop and the onboard controller for the internal sata drive has gone bad. I do have a drive in there (bought new because I had assumed it was the drive that had gone bad) which is probably unformatted. Gparted can't see it, so I tend to assume it is irrelevant. I boot from an external usb sata drive that is designated by the system as sda. I have 3 other similar Ubuntus and a PClos on the same drive and they all boot fine. And this system did boot fine until today. I can reinstall it of course, but if anyone can think of any simpler fix that might work, I'd appreciate a suggestion.

Thanks for reading.

---

### Post by sudodus on 2015-12-15
Maybe removing the drive connected via SATA will make things work again.

Have you tried booting from another USB drive (any kind: live, persistent live or installed)?

Have you tried booting from all the USB connectors of the computer?

-o-

It could be some hardware component failing (for example the SATA controller failing more than before), or it could be a problem with the USB boot drive (a damaged file system or an update that broke the system).

---

### Post by Dreamer Fithp Apprentice on 2015-12-15
Thanks, Sudodus.
I tried switching the drive to another usb port first. That didn't change anything, but as I stared at the error messages, a tinker's inspiration struck and I cntrl-alt-F3'ed, logged in and used startx. Everything worked normally. So I purged lightdm and the greeter and reinstalled them. That fixed it.

---

### Post by sudodus on 2015-12-15
Congratulations :-)

---

### Post by Dreamer Fithp Apprentice on 2015-12-19
UPDATE: There's a better way !!!!!
This happened to me AGAIN, but this time I got closer to figuring out why. With lightdm-gtk-greeter there are files in /usr/share/lightdm/lightdm.conf.d/ that can be used to run commands or call scripts after X starts but before you login. I use one of them, 60-lightdm-gtk-greeter.conf, to call a script by setting a variable like so```
greeter-setup-script=path/scriptname
```I commented out that line and the problem went away. Purging and reinstalling lightdm-gtk-greeter solved the problem before, NOT because the greeter code was corrupted, but because it puged my modified config file calling the script. And when I restored the config file, it broke again. So I switched to a script that just said ```
exit 0
``` and that worked fine also. I switched to a backup of an earlier version of the script made when I last edited it and that also worked fine. Unfortunately, I then got into improving it through several iterations, each making a backup automatically, and I've lost track of which version broke it, but I'd have to presume I introduced some error in the script earlier that either made it exit with a non-zero exit code, or, more likely, stuck it with an endless loop or a debugging read -p I forgot to remove when I finished testing it in a terminal. I haven't a clue why that resulted in that particular error message, but it seems to have been the problem at any rate. So, anybody finding this thread with a similar problem, you might check that first.

---

