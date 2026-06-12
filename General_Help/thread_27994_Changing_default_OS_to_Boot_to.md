---
title: "Changing default OS to Boot to?"
date: 2005-04-18
forum: General Help
---

### Post by Boopop on 2005-04-18
At the moment the grub booter boots linux if i dont say otherwise within 10 secs. How can I configure it so it default boots to windows?

Thanks in advance,Boopop

---

### Post by bored2k on 2005-04-18
Two methods (I like B):

A) [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)
B) sudo apt-get install grubconf :
[img]http://img25.echo.cx/img25/7489/screenshotgrubconf6gc.png[/img]

---

### Post by jerome bettis on 2005-04-18
from a terminal type
sudo gedit /boot/grub/menu.lst

then you can either set the default option (near the top) from 0 to whatever number windows is (if it's the third choice on the menu, then set this to 2).

or you can go all the way down to the bottom and swap all of the lines for the windows choice up to the top of the list.

---

### Post by Boopop on 2005-04-18
[QUOTE=bored2k]Two methods (I like B):

A) [http://ubuntuguide.org/#changedefaultosgrub](http://ubuntuguide.org/#changedefaultosgrub)
B) sudo apt-get install grubconf :
[img]http://img25.echo.cx/img25/7489/screenshotgrubconf6gc.png[/img][/QUOTE]

I tried the second method u suggested, and the terminal said there was no installation candidate :???:

---

### Post by Boopop on 2005-04-19
Bump

---

### Post by Sabator on 2005-04-19
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories) should solve most problems you have with not finding packages.

---

### Post by Fab on 2005-04-19
grubconf isnt in any of the repos (hoary, hoary-updates, hoary-security, backports, marillat, universe and multiverse enabled where possible)

---

### Post by bored2k on 2005-04-19
I know it's in Universe because that's were I got it from [[http://security.ubuntu.com/ubuntu/pool/universe/g/grubconf/]](http://security.ubuntu.com/ubuntu/pool/universe/g/grubconf/]), but here's another option

[http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/)

---

### Post by Fab on 2005-04-19
[QUOTE=bored2k]I know it's in Universe because that's were I got it from [[http://security.ubuntu.com/ubuntu/pool/universe/g/grubconf/]](http://security.ubuntu.com/ubuntu/pool/universe/g/grubconf/]), but here's another option

[http://www.metallikop.com/ubuntu/](http://www.metallikop.com/ubuntu/)[/QUOTE]
 i cant find it via synaptic or apt-get
and yes, i do have universe nad all the other extra repos enabled Oo

---

### Post by Fab on 2005-04-19
well, i installed the .deb package manually (needed to grab a dependency first, which was in the repo)
worked out pretty well, except that when running it from the menu entry it will say "you must run this application as root" instead of asking me for the password, but i can live with that :)

---

### Post by Bob D. on 2005-04-20
[QUOTE=Fab]grubconf isnt in any of the repos (hoary, hoary-updates, hoary-security, backports, marillat, universe and multiverse enabled where possible)[/QUOTE]

Try here: [http://archive.ubuntu.com/ubuntu/pool/universe/g/grubconf/]("http://archive.ubuntu.com/ubuntu/pool/universe/g/grubconf/")

Bob

*EDIT: Have been trading emails with one of the MOTU (Masters of the Universe) maintainers. He tells me that grubconf was removed from the Hoary Universe repo to the archive (hence, the archive in the URL above). So no way to get at it from the normal repos. He didn't say why it was removed, only that it is in Breezy and a minor bug fix (using gksudo on the EXEC line in the .desktop file) will be incorporated.*

---

