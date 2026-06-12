---
title: "Xorg configuration broken"
date: 2006-12-27
forum: General Help
---

### Post by Xbehave on 2006-12-27
ive been running kubuntu 6.10 edgy for a while (2/3 months) and it runs fine (most of the time) but everytime i run alot of programs ( including firefox,leafpad and most) in console i get the following error
```
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  143
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

```
x2
but the program still runs fine

only recently i have got the chance to play some games however i didnt have GLX running properly
```
 OpenGL GLX extension not supported by display ':0'
```

however all the autoconfigures fail and i was wondering what i should do to get the original error fixed?
i can give more details and errors and know my way around linux basics quite well but i thought id make a relativly short 1st point

---

### Post by meng on 2006-12-27
One way of fixing the xorg.conf is to run from terminal:
sudo dpkg-reconfigure xserver-xorg

---

### Post by Xbehave on 2006-12-28
when i use that i get the same error as above only 4 times instead of 2, followed by
```
Use of uninitialized value in join or string at /usr/share/perl5/Debconf/DbDriver/Stack.pm line 104, <GEN6> line 13.
xserver-xorg postinst warning: not updating /etc/X11/X; file has been
   customized

```
which i assume might be because i used automatics and easyubuntu when edgy was 1st out

then when i get to choosing colour depth and sync ranges, the program crashes and says:
```
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20061228171536
dexconf: error: cannot generate configuration file; shared/default-x-server not
set.  Aborting.  Reconfigure the X server with "dpkg-reconfigure" to correct
this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration
Use of uninitialized value in substitution (s///) at /usr/share/perl5/Debconf/Format/822.pm line 83.
Use of uninitialized value in concatenation (.) or string at /usr/share/perl5/Debconf/Format/822.pm line 84.

```

p.s sorry about the delay in reply i didnt realise how fast these forums were.
i also get an error when i run the nvidia script but i dont no if thats due to the xorg being wrong in the 1st place

---

### Post by meng on 2006-12-28
Automatix AND Easyubuntu? I'm not sure I can help you out, this seems complicated. If you know what you're doing you can manually edit the xorg.conf:
sudo nano /etc/X11/xorg.conf
or else use your favorite editor.

You can change the video driver (one option is to go with the generic "nv" if you have an nvidia card) and also the color depth and sync ranges.

However, others have reported, and I've experienced it myself occasionally, that when they do the manual edit the changes don't stick. I can't explain why this happens.

Best of luck, but I suspect you'll need someone else to volunteer their services for this one.

---

### Post by Xbehave on 2006-12-28
i think i can edit my xorg but id like to know as much before as possible. are there any guides?
what should i do with sync ranges? (i no nothing about them)
what part of the xorg is broken?
i think its the graphics but im not sure?

i think i can get the changes to stick i fixed an old xorg config (by switching it with a backup) off a live CD that seams to always keep changes.
actually if i find out what part is broken i can simply restore the 1st backup thats not broken right? so from the errors is it clear whats wrong?

---

### Post by Xbehave on 2006-12-29
ok i think ill have a read and fix my xorg but i just noticed that the 2nd set of errors are about
debconf
and that reminded me that i tried 3 different repo managers (i just didnt like adept) and maybe 1 of them has changed my debconf which has inturn messed up installs?
 is this possible?
how would i go about fixing it?

UPDATE:
i ran dpkg-reconfigure debconf to fix my debconfig
then dpkg ran fine on  sudo dpkg-reconfigure xserver-xorg
which means everything now runs fine
BUT my original error still happens when i run programs like leafpad or firefox from console! could some1 explain xorg abit so i can look for the problem?

---

