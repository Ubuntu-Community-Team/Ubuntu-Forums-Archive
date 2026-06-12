---
title: "Xunbutu crashes when accessing  terminal"
date: 2007-12-30
forum: General Help
---

### Post by revelationman on 2007-12-30
First off I  run a Compaq Deskpro C733 with 192 megs of ram i believe it is with  the  810 chipset 

Okay  I am newwith linux and I decided to run a few basic commands nothing major just to learn , 

I click on   the box for terminal  then bang  the screen goes all different  colours then   it goes back to the  login box 

Other then that   the system works  this is my  test machine for linux  I will invest in some more ram and maybe a  higher grade video  card 

But anyone has any suggestions 

Thanks

---

### Post by p_quarles on 2007-12-30
That doesn't sound like much fun. 

Anyway, I can suggest a few things to try:
Open the "run" dialogue (alt-F2) and type the following:
```
xfce4-terminal
```
My guess is that the same thing will happen, but try it anyway.

Next, open the run dialogue again and type:
```
xterm
```
This is a more basic terminal program. If this opens, try running the Xubuntu terminal from within Xterm by typing (again):
```
xfce4-terminal
```
You will almost certainly get the same result as you did in the first step, but you also may get a chance to see the specific error output before the GUI crashes. If you can make out any of what it says, be sure to post it here. 

Finally, there are a number of other alternative terminal programs that more versatile than Xterm. You can look in the package manager for any of these:
gnome-terminal
aterm
mrxvt
rxvt-unicode
eterm
konsole
pterm

Personally, I use [Sakura]("http://pleyades.net/david/sakura.php"), which is not available in the repositories, but is easy and quick to compile.

---

