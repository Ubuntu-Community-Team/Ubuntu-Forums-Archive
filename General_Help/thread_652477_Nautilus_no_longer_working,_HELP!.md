---
title: "Nautilus no longer working, HELP!"
date: 2007-12-28
forum: General Help
---

### Post by Gigamo on 2007-12-28
```
gigamo@GIGAMO2:~$ nautilus
nautilus: error while loading shared libraries: libbeagle.so.0: cannot open shared object file: No such file or directory
```

This is what I get! The only thing I did was install Cedega (i was running fluxbox, then i went ctrl-alt-backspace and chose gnome again, and nautilus did not automatically start up anymore and it doesn't manually either!)

Help please :(

When I try
```
sudo apt-get install libbeagle0
```

It says that libbeagle0 is already the newest version. And when I try to uninstall it (to reinstall) it also wants to uninstall nautilus.

---

### Post by AlCali on 2007-12-28
Hi,
i have the same problem since 2 hours (and since the last reboot after the last recomm. update libeagle...) 

no solution so far...


My system: Ubuntu 7.10, Ati Xpress on board.

---

### Post by Gigamo on 2007-12-28
Thank god, I solved it.

I noticed that it was saying "schmidtke" in synaptic, where it says "installed version". That must have come from the repo I added to update pidgin and gimp. I then clicked on Package -> Force Version and selected the default (gutsy) version. It then downgraded and now nautilus is working again.

---

### Post by Anduu on 2007-12-28
You got lucky there....be very careful with third party repos.

The first thing I do when I add a repo for some software I want is I do a sudo apt-get update/upgrade ***_[COLOR="Red"]before[/COLOR]_*** I install the software I'm looking for.If anything wants to be upgraded I immediately remove that repo and forget it ever existed.

---

### Post by squee on 2007-12-29
I have posted a more concise solution here

[http://ubuntuforums.org/showthread.php?p=4036441#post4036441](http://ubuntuforums.org/showthread.php?p=4036441#post4036441)

Slightly easier to follow for someone (like me) who hasnt a clue sometimes!

~Squee

---

