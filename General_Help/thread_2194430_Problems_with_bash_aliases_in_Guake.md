---
title: "Problems with bash_aliases in Guake"
date: 2013-12-18
forum: General Help
---

### Post by xeneize--86 on 2013-12-18
Hello,

I have ubuntu and i have been running commands from bash_aliases file without problems from terminal, but when i try to run this command from Guake terminal, it doesn't works.

I appreciate help with this problem

My ubunutu version is:
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise


Thank you!

---

### Post by xeneize--86 on 2013-12-18
I found a solution, but i don't like so much.

I edited guake.desktop file with:
sudo vim /usr/share/applications/guake.desktop

And in the line:
Exec=guake

I changed it for this:
Exec=guake -e $SHELL

I can't understand why it is neccesary.

---

### Post by steeldriver on 2013-12-18
Did you try running guake-prefs and checking that the 'Default interpreter' is set to '<user shell>'? Is your login shell set to /bin/bash?

---

### Post by xeneize--86 on 2013-12-23
I checked my default interpreter and it was set as you said (user shell).

Anyway, i found the problem.

The problem is fixed.

I think that when i was 'playing' with virtualenvs, i accidentaly touched .profile file, and that caused the problem. I think that, because at next day when i turned on my computer, i had some login errors. And now, when when i put my file guake.dektop file like original it works well.

anyway, Thank you for the help!! :)

---

