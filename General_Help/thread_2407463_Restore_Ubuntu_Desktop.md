---
title: "Restore Ubuntu Desktop"
date: 2018-12-04
forum: General Help
---

### Post by mabs2 on 2018-12-04
Hi 
I need some help to restore my ubuntu-desktop to the default.
I installed Kubuntu-Desktop from tasksel and now i cant remove it.
Every command I use to try fix this it give depencies error.
Sombody Help PLS.

---

### Post by deadflowr on 2018-12-04
> Every command I use to try fix this it give depencies error.
Post the output from the commands you've used.

---

### Post by mabs2 on 2018-12-04
[IMG]https://imgur.com/a/iTTkfWg[/IMG][https://imgur.com/a/iTTkfWg](https://imgur.com/a/iTTkfWg)

---

### Post by ajgreeny on 2018-12-04
Use command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
``` to see a list of all packages installed by date and time.

From that list you can find the kubuntu-desktop package and see everything else that was installed at the same time and should give you a list of all those that you now need to remove to get rid of the full kubuntu-desktop plus its dependencies.

Go one grep further with ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log | grep kubuntu-desktop
``` and it will save you time searching for the date it was installed and you could help even more if you grep for the date shown as well; have a look at **man grep** in terminal and come back to ask for more details if that doesn't help and you still you don't know how to use grep.

---

