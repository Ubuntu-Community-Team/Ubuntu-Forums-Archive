---
title: "Software Centre Problem"
date: 2013-05-31
forum: General Help
---

### Post by roly33 on 2013-05-31
I'm unable to install anything from the Software Centre or from .deb files on my 13.04 x64 after trying to install Kingsoft Office. I just get a red dot with a white line through it on the Notification bar, with an error saying that kingsoft office needs to be reinstalled but the archive can't be found wich usually means un met dependancies, but the .deb file is sitting on my desktop and when I tried to install there was no dependancy issues showing in Software Centre.

How can I fix this without having to do a clean reinstall?

Roland

---

### Post by ohnonot on 2013-06-01
the fact that the deb sits on yourdesktop means that you did not install it through software center, but downloaded straight from your browser and double-clicked it, right?
something must have gone wrong there.
i think it's best if you get aquainted with packet management and apt-get, which i think is still the underlying tool under all gui packet installation apps (software center).
in a terminal, type 'man apt-get' and try to find options like clean, autoclean, repair... which you then can try out. so the command line would be something like ```
sudo apt-get autoclean
```(i'm guessing now, i'm writing this from another install that does not use apt-get so i can't check).
it probably won't be enough but will produce output that will help you understand the problem better.

---

### Post by ibjsb4 on 2013-06-01
Where did you find the .deb download?  The Kingsoft site has downloads for Windows and Android.

---

### Post by adan-j93 on 2013-08-15
I had the some problem for a few months, finally i found a forum that helped me

i dont actually know what's going on but here's what I used:

sudo dpkg --remove --force-all kingsoft-office

if that doesnt work, try this:
# become root
sudo -i
cd /var/lib/dpkg/info
rm -rf hl1440lpr*

dpkg --remove --force-remove-reinstreq kingsoft-office


okay I used that and it didt worked! but it said that i should try to purge...so i did it:

sudo apt-get purge kingsoft-office

after a few moments the red dot with the line disappeared!

---

### Post by yonice.perez on 2013-12-14
[COLOR=#000000]Try:

dpkg --**purge** --force-remove-reinstreq [/COLOR][COLOR=#417394]kingsoft-office[/COLOR]

---

