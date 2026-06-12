---
title: "help me to install flash player 9"
date: 2008-03-08
forum: General Help
---

### Post by timetoballj on 2008-03-08
every time i try to install the player it tells me to remove the zpti.dat frome the componets directory of the mozilla browser

---

### Post by NightwishFan on 2008-03-08
I believe you can install flash from the repos using:

sudo apt-get install flashplugin-nonfree

---

### Post by timetoballj on 2008-03-08
thanks but i am not really sure how to get to that i have only been using gnome about a day

---

### Post by NightwishFan on 2008-03-08
Its fine. :)

For me Ubuntu seems to take care of me. Rather than install it from a remote source use the one in the repos.

Close Firefox

To open a terminal. Press alt+f2 and type:
gnome-terminal

When in the terminal type:
sudo apt-get install flashplugin-nonfree

It will ask for password, but not appear to type. Do not worry it is. Just type your password. If you make a mistake you can invisibly backspace.

It will install. When it is done, reopen firefox and you are good to go.

---

