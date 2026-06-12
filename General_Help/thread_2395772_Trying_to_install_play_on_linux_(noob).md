---
title: "Trying to install play on linux (noob)"
date: 2018-07-06
forum: General Help
---

### Post by wigglyjames on 2018-07-06
iv been puuling my hair out trying to figure this out, would really appreciate if someone could help.
here's whats happening.


wiggles@wiggles-Aspire-F5-573G:~$ sudo apt-get install playonlinux
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 playonlinux : Depends: wine or
                        wine-development but it is not going to be installed
               Depends: python-wxgtk3.0 but it is not going to be installed
               Depends: cabextract but it is not going to be installed
 steam-installer : Depends: steam (= 1:1.0.0.54+repack-5ubuntu1) but it is not installable
 wine-stable : Depends: wine-stable-i386 (= 3.0.2~bionic) but it is not installable
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

---

### Post by yancek on 2018-07-06
Have you tried running the command suggested in your posted output?  If so, what happened?  The other messages are telling you that there are dependencies, other software that is necessary for playonlinux which you will also need to install.

---

### Post by oldos2er on 2018-07-06
What is the output of ```
sudo apt update && sudo apt install -s wine-stable
``` ?

---

