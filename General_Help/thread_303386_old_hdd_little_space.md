---
title: "old hdd little space"
date: 2006-11-20
forum: General Help
---

### Post by feest on 2006-11-20
hi, i want to run a home based webserver on ubuntu because i recently found an old hdd that runs ubuntu (i already had a webserver), the problem is that i have little space on the disk so i want to remove big things as open office. but when i try to do that it says it needs to remove gnome. is there any way te remove open office without gnome?

(the old hdd i found is running breezy badger)

---

### Post by reclusivemonkey on 2006-11-20
> **feest said:**
> hi, i want to run a home based webserver on ubuntu because i recently found an old hdd that runs ubuntu (i already had a webserver), the problem is that i have little space on the disk so i want to remove big things as open office. but when i try to do that it says it needs to remove gnome. is there any way te remove open office without gnome?

(the old hdd i found is running breezy badger)

Why do you need gnome on your web server? If you want to run a webserver then I would suggest using the Server version of Ubuntu. I believe this does not include X or any "desktops" such as KDE/Gnome. If you are running a webserver, you want as much of the PC's resources dedicated to this rather than running a desktop. I run my webserver on Slackware without X which is the same principal. I should imagine there are various threads on this if you search the forum.

---

### Post by feest on 2006-11-20
well i manage a lot of files on it and i don't like to work blindley so thats why i prefer to have gnome one it

---

### Post by reclusivemonkey on 2006-11-20
> **feest said:**
> well i manage a lot of files on it and i don't like to work blindley so thats why i prefer to have gnome one it

You can share the files with NFS or SSH via Gnome and use Nautilus on your desktop to manage the files. This also means you don't need to have a monitor attached to the server which saves power.

---

### Post by anaconda on 2006-11-20
It doesn't really remove gnome.
I think you mean the meta package called gnome-desktop (or something hope I remember the name correctly)

If you remove gnome-desktop it wont remove your gnome. Really. It just means that OO depends in that metapackage like some other programs.

If you dont believe then try for yourself. OO and gnome aren't tied together THAT hard.  :)

EDIT:
The name of the meta package that I meant was: ubuntu-desktop
here is a link, where aysiu explains what meta-package means.
[http://www.ubuntuforums.org/showthread.php?t=289468&highlight=gnome-desktop+package+remove](http://www.ubuntuforums.org/showthread.php?t=289468&highlight=gnome-desktop+package+remove)

---

### Post by feest on 2006-11-20
so and when i remove gnome i can easily reinstall it with apt-get install ubuntu-desktop right?

---

### Post by carlosqueso on 2006-11-20
no, what anaconda means is that uninstalling openoffice **will not uninstall** GNOME.  If you install ubuntu-desktop you WILL reinstall openoffice.

---

### Post by deanlinkous on 2006-11-20
:)

---

### Post by feest on 2006-11-20
but when i uninstall openoffice i will uninstall ubuntu-desktop not gnome-desktop so it will remove my gui right.

---

### Post by deanlinkous on 2006-11-20
more than likely the ubuntu-desktop package is made up of other packages and that is all it is...
So ubuntu-desktop is a package that specifies the following packages
gnome
openoffice
clearlooks
XYZ
ABC

So by uninstalling openoffice it will remove the desktop package because the ubuntu-desktop package is simply a list of other packages and you are removing one of them. I cannot imagine it would remove ALL of gnome.

---

### Post by carlosqueso on 2006-11-20
deanlinkous is correct as long as you use apt-get and not aptitude to do the uninstalling.  ubuntu-desktop is perfectly safe to remove.

---

### Post by feest on 2006-11-20
well lets try it if not, i try apt-get install ubuntu-desktop :P

---

### Post by feest on 2006-11-20
okay i uninstalled it but i don't see anymore room on the disk since my last check this may be cause because i also installed some updates but i can't imagine thats so much so is it completely removed or not active

---

### Post by deanlinkous on 2006-11-20
Then you will reinstall everything that it includes which would also be openoffice.

If you need to install anything after removing openoffice (you wont) then just install gnome.

Some packages (like ubuntu-desktop) are called meta-packages and they just list other packages to install and when you uninstall one of those then the metapackage is removed also but it isn't anything functional.

---

### Post by feest on 2006-11-20
but is it removed or not active because i don't have much space more its actually equal

---

### Post by tubasoldier on 2006-11-20
If that is the case try removing other software you will not need on a server. I'm sure with uninstalling open office and then installing apache/mysql/php you may have installed about the same amount of software. 

Or it could be that you only removed the ubuntu-desktop package. Its very small because it is only a list of packages to have installed. Uninstalling it does not mean that all packages installed because of it will be removed. Open up synaptic and search for open office. mark them to remove completely. Also remove any programs you wont use, Rhythmbox for instance, gaim, games, gimp, xsane... then hit the apply button. You should notice much more available space.

---

### Post by carlosqueso on 2006-11-20
also try ```
sudo apt-get clean
``` to get rid of archives that may be hanging around your system.  you may have OpenOffice sitting there still.

---

