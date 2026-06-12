---
title: "Open Source Drivers Installation Instructions..."
date: 2014-01-19
forum: General Help
---

### Post by Random258 on 2014-01-19
Hi everyone! Probably a stupid question but I was wondering where can I manually install the Open Source Drivers for AMD Radeon cards. My gpu is a Saphire Radeon HD 6670 which I checked it is supported...(pretty sure..maybe I read wrong). I've been struggling for about 3 straight weeks now to get the thing working using the propietary drivers with only minor success..(about 3 times it got to work but with such laggyness that it was unusable and blackscreen after logging in). I know that there is one that comes pre-installed on to Ubuntu 12.04 ( I believe so correct if I'm wrong ) but it hasn't really worked...I just get to see the boot up for Ubuntu with the 4 dots then a constant loop of screen on - flicker - then dead, repeat. Links to any guides would be great! Also please tell me which dependencies and things that I should add ( I read somewhere about linux-generic... but could never get it the files wayy too many to choose from while I was looking at the list in the terminal screen ). I'm getting fairly desperate...I've done at least 6 different re-installs using Ubuntu 12.04, 12.1, 13.04, 13.1 and ZorinOS ( basically Ubuntu 12.04 ) so any help at all would be great.
THANK YOU! :D :D :D :D :D

Things I Would REALLY Like..
- Ability to use Ubuntu + Desktop + GUI in general with no problems and fairly smoothly..
- Ability to play some games...minecraft and hodgepodge (spelled wrong probably sorry everyone...) of steam games

---

### Post by deadflowr on 2014-01-20
You already have the open-source drivers.:)

But it seems like you might need to do little more.
Have you tried setting nomodeset in the grub?

When you first boot up, enter the grub screen.
(This is usally done by holding, I think, the shift key right when the first BIOS(usually the first screen that loads, the one that usually says somewhere on it "open syste setting press F1, or something like that)
Anyway, you hold the key down until the grub loading comes up and let go
now you should have the gub menu.
press e, to edit and now in the editor add nomodeset to line with what is usally there "quiet splash"
so instead of quiet splash, it should look like quiet splash nomodeset

When done, follow whatever option it lists to save, and/or save and exit, then try loading Ubuntu by selecting the first option in grub, and press enter.


If by chance getting into the grub screen proves hard, try this.
Boot as normal and when the screen stops working, press ctrl+alt+F1
now you should get terminal like console.
login like you would normally, put your username and password.
(remember password fields remain unseen, so type it as good as you can.)
Now once logged in, run
```
sudo nano /etc/default/grub
```
enter the password again.
now change the entry
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
```
to this
```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
```then press ctrl+x, enter y and the hit enter again.
this should save the new entry.
then run
```
sudo update-grub
```


let it run and now try a reboot
either
```
sudo reboot
```
or
```
sudo shutdown -r now
```

See what happens.
Good Luck.

---

