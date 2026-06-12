---
title: "wine problem"
date: 2007-06-19
forum: General Help
---

### Post by tango11 on 2007-06-19
Feisty noob
have downloaded wine with synaptic when I try to run config screen lock activates and returns to log in screen any help appreciated

---

### Post by Qu4k3R on 2007-06-19
Update wine:

> 
sudo apt-get update
sudo apt-get install wine


Then just execute winecfg in the terminal.

---

### Post by tango11 on 2007-06-19
thanks have tried that ,wine has been installed but disappeared; when I try to configure or open from terminal screen locks down and reverts to login screen. Help!

---

### Post by tango11 on 2007-06-20
I have solved the problem myself after reading through pages of threads  i noticed there seemed to be a common problem with the screen saver in feisty locking down and not allowing access from sys menu screen saver was also locking me out of gnome and taking me to login screen. i found numerous threads with similar probs in one reply some one said upgrade video card drivers
All of a sudden the light came on went to synaptic and upgraded myVoodoo 3fx by installing
glide2bin +libglide3 end all problems
my advice upgrade your particular video card
And thanks to whoever it was that suggested this in one of the threads:D:D:D
ps install wine through gnome prob also solved by same solution as screen saver is not locking me down halfway through

---

### Post by Cogman on 2007-06-20
You might want to change where you get wine from as well. Ubuntu's wine is starting to age and stink a little (they are like 0.9.33) wine hosts a fiesty respritory.  Here are the commands straight from winehq.com (the wine home)

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list](http://wine.budgetdedicated.com/apt/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/winehq.list

---

### Post by tango11 on 2007-06-20
Thanks  mate already got it from there but thanks anyway

---

