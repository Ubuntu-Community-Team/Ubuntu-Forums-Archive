---
title: "restore default python set up on ubuntu 18"
date: 2020-09-03
forum: General Help
---

### Post by NotQuiteSU on 2020-09-03
I'm running Ubuntu 18.04.5 LTS, and due to some crap circumstances, I had to purge python3 from my system.  What would be the best way to restore the 'default" python3 set up which came with a clean Ubuntu 18.04.5 LTS install?

---

### Post by CelticWarrior on 2020-09-03
Perhaps a clean install of the OS is the better and faster option.
Furthermore, there aren't any circumstances that make users purge an essential part of the OS, so essential that it can't work without it. Next time post your problem before doing absurd things.

---

### Post by NotQuiteSU on 2020-09-03
I had an app was having issues with Python3, and I didn't have anything else that relied on Python3, so I did an apt remove. I'm up and running, but I was hoping to just restore Python3. A clean install would be nice, but I sadly don't have the time to do that. i may go the other option and go to 20 LTS

---

### Post by CelticWarrior on 2020-09-03
If you don't have the time to do a clean install then certainly you don't have the time to install it back. It takes a lot of effort and is time consuming because the native tools for installing stuff depend precisely on the packages you removed. 

> [COLOR=#000000]I had an app was having issues with Python3, and I didn't have anything else that relied on Python3[/COLOR]
Is this supposed to be a joke or something? Pretty much all the core OS functionalities depend on it!

---

### Post by Impavidus on 2020-09-04
The python3 package is (almost) a metapackage. There's (almost) nothing in it, but it pulls in some other packages that together give a working Python 3 install. Also, some other packages depend on python3 to get this working Python 3 install. So you can purge python3 with dpkg, which will lead to missing dependencies, but your system will still work. If you manage to remove python3 without getting dependency issues (removing everything that depends on python3), you will break your system. If you remove all of Python 3, it will be even worse.

---

