---
title: "Sharing /home with another distro"
date: 2007-04-15
forum: General Help
---

### Post by rekahsoft on 2007-04-15
Hi all, i am going to install Fedora 7 test 3 as a Gnome development system (so i do not muck up my ubuntu) and i want to share my /home. I have heard mixed opinions about this...is it ok? If i were to do it i would have the same username, UID, and /home folder name on both the ubuntu install and the fedora install. I would also have a separate partition mounted as /home in each distro. Would all go well? 

Note that i plan to build gnome from source on the fedora install...could that cause problems?

---

### Post by bapoumba on 2007-04-15
Hello,
I'm not sure this would work, packages may not be at the same version level between Fedora and Ubuntu, and you may have problems with conf files.

---

### Post by ScottMorris on 2007-04-15
I'm sure this is possible.  I have heard of cases where people do use different distributions on the same machine.  I have used Ubuntu 6.10 and Xubuntu 6.06 together with no problems but that may be because they are both Debian based derivatives of one another.

I know that Fedora used 500 as its starting User ID and Ubuntu uses 1,000.  Not sure what kind of effect this would have.  The home folder name would be the same if you made your username the same of both OSs and you pointed the user to the directory that you want to be the home (either using the usermod command or the Graphical Utility.)

---

### Post by rekahsoft on 2007-04-15
> **ScottMorris said:**
> I'm sure this is possible.  I have heard of cases where people do use different distributions on the same machine.  I have used Ubuntu 6.10 and Xubuntu 6.06 together with no problems but that may be because they are both Debian based derivatives of one another.

I know that Fedora used 500 as its starting User ID and Ubuntu uses 1,000.  Not sure what kind of effect this would have.  The home folder name would be the same if you made your username the same of both OSs and you pointed the user to the directory that you want to be the home (either using the usermod command or the Graphical Utility.)

lol thanks scotty :P i am still a little hesitant..but hey..i have never done it before. I will be sure to backup first :D

---

