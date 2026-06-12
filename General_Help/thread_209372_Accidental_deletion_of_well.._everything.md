---
title: "Accidental deletion of well.. everything"
date: 2006-07-05
forum: General Help
---

### Post by krazykirk on 2006-07-05
Hi there all,

I was installing a package needed for VNC to work, but it said that there was a unsolved dependency (X something server or something?) and i was just like Yes install without really looking though it, and it managed to remove most of my packages!!!

I really need help with some way of getting my packages back installed on my system! (I'm in windows and i'm not liking it) Apt-get seems to have removed them so is it possible that the package files are still on the system and I could install it back?

I would rather not have to download all my files again but i could if i really needed to.

Thanks! =)

---

### Post by Dr. Nick on 2006-07-05
apt-get caches alot of them, so redownload may not be necessary. 

If you get booted into a command line then try this to reinstall  most of the default packages and hopefully restore a gui

sudo apt-get install ubuntu-desktop

---

### Post by krazykirk on 2006-07-05
ok cool thanks! I'll try that and see how that goes

---

### Post by krazykirk on 2006-07-05
hmm it didn't quite work... I got booted into a command line so I tried
sudo apt-get install ubnutu-desktop

and I got this huge list of dependencies! (Probably all the other packages that got deleted) Is there a command that will let me install those dependencies at the same time?

---

### Post by mcduck on 2006-07-05
apt-get *will* install all dependencies with the ubuntu-desktop package :)

---

### Post by krazykirk on 2006-07-05
but after the list of dependencies there was a error (E:Something) so it didn't work...

---

### Post by patrickfromspain on 2006-07-05
Try sudo aptitude install ubuntu-desktop

---

### Post by krazykirk on 2006-07-05
ok thanks! i'll try it now

---

### Post by krazykirk on 2006-07-05
hmm it doesn't work... I tried sudo aptitude install ubuntu-desktop, then it loaded the list of dependencies, then it said Resolving Dependencies... Open: XXX; Closed: xxxx; Defer:xxxxx; Conflict:xxxx

Then after a while it said No solution found within the alotted time. Try harder? [Y/n].

I did that a lot of times, and it didn't come up with a solution. what should i do?

---

### Post by Dr. Nick on 2006-07-05
Are you able to download packages, Or do you not have internet.

What part of the problem may be is that the vesions you had are not the newest anymore, maybe a update has come since then so the version you had isnt on the servers anymore.

you could try this command if you have internet connection

sudo apt-get update

The manner on how that runs may help diagnois the problem.


I havent seen a error like that in awhile, hopefully someone else has other ideas to try aswell

---

