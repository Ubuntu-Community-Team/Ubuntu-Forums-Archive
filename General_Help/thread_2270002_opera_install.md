---
title: "opera install"
date: 2015-03-19
forum: General Help
---

### Post by trav9595 on 2015-03-19
Whenever I download stuff from the web  and I clik on it to install, it opens the Ubuntu software center. I DONT want that to happen...
how can I get RID of that script.... I  want to open debian files and simply install them on my PC...

---

### Post by kerry_s on 2015-03-19
software center is used to install by default. you can install another app to do the job.

sudo apt-get install gdebi
or
from the terminal the command is:
sudo dpkg -i name-of.deb

---

### Post by deadflowr on 2015-03-19
Following kerry_s' suggestion of installing and using gdebi.
After you install gdebi, right click on any .deb file and go to properties >> open with and select gdebi and set it as the default.
From then on, any double click on any deb file will open the gdebi program, instead of the software center.
(Or at least, it should)
> I want to open debian files and simply install them on my PC...
That's what the software center is doing.
deb files are package installation files, which contain installation scripts which will correctly install the packages that it has.
They are designed to automate the installation of otherwise arcane(to the normal user) packaging structures. If that makes sense.

Edit: I realized this is about xfce, which means it probably has another method or name to set the preferred applications to launch...
Though i think it is more or less the same concept.
(I'm used to nautilus over thunar, so there is that)

---

### Post by amanchesterman on 2015-03-19
Yes as deadflowr says, it's the same principle in Thunar. Right click on the .deb package and Thunar offers to open it with Software Center as the default, but there's also the option 'open with another application'. Choose that, and you can select any installed application and set that as the default for opening .deb packages in future.

---

