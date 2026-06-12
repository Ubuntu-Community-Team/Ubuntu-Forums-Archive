---
title: "Mintmenu  cannot launch applications"
date: 2013-08-08
forum: General Help
---

### Post by nobody92 on 2013-08-08
Hello,

 I have Xubuntu 13.04 installed and I want to use mintmenu(because it's the one I'm most used to). So I added the Linuxmint Nadia repos to **sources.list** (deb [http://packages.linuxmint.com/](http://packages.linuxmint.com/) nadia main upstream import) and installed mintmenu with all its dependencies.

The problem is mintmenu won't launch any of applications(neither from the favorites panel or any other). Only the default ones on the left side: Computer / Home folder / Desktop / etc. So I launched it from a terminal to see why it isn't working, and tried to launch Google Chrome. The output was the following:
> 
*********** Keybind Driver Load Failure **************
Error Report :  No module named deskbar.core.keybinder
Opacity is: 98
Setting opacity to: 0.98
__init__ took 67.487 ms
Binding to Hot Key: <Control>Super_L
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'bind_key' is not defined
/
o
p
t
/
g
o
o
g
l
e
/
c
h
r
o
m
e
/
g
o
o
g
l
e
-
c
h
r
o
m
e
 
%
U
[Errno 13] Permission denied


The problem is that it adds a newline after each symbol, so the actual output, for a working menu, should have been something like:
> 
*********** Keybind Driver Load Failure **************
Error Report :  No module named deskbar.core.keybinder
Opacity is: 98
Setting opacity to: 0.98
__init__ took 67.487 ms
Binding to Hot Key: <Control>Super_L
** WARNING ** - Menu Hotkey Binding Error
Error Report :
global name 'bind_key' is not defined

/opt/google/chrome/google-chrome %U


Does anyone know how if I could solve this problem? And if so, **how** can I solve this problem? Thank you in advance.

---

### Post by Frogs Hair on 2013-08-08
I only find instructions for 12.04 , so I don't know  that the mint menu  will work in versions after that . [http://xubuntugeek.blogspot.com/2012/07/how-to-install-mint-menu-in-xubuntu.html](http://xubuntugeek.blogspot.com/2012/07/how-to-install-mint-menu-in-xubuntu.html)

---

### Post by gordintoronto on 2013-08-08
Have you tried installing Mate or Cinnamon, then selecting it at boot time?

---

### Post by nobody92 on 2013-08-09
@Frogs Hair: That's the way I installed it, only replaced the maya repos with nadia(maya repos had the same problem).
@gordintoronto: I have, it works on mate, but that's not why I installed Xubuntu. I wanted to use XFCE, bein much more lightweight than other DEs.

---

### Post by pqwoerituytrueiwoq on 2013-08-09
mint menu in xfce uses a applet that lets mate applets run in xfce, there is probably a unlisted dependency, try looked for related packages in synaptic

---

### Post by tdockery97 on 2013-08-09
I don't think you can install it in 13.04.  Mint discontinued the xfce plugin for mint menu starting with Mint 15 Xfce.  They now use the Whisker Menu as the default menu.  It is a little similar to mint menu but less gaudy.  If you really want the old mint menu in Xfce it would be better to use Xubuntu 12.10, as you should be able to install it from the Mint Nadia repo without the dependency problems.

---

### Post by nobody92 on 2013-08-09
Okay, so that means I have to find another menu to use. I tried installing whiskermenu both by adding the repo, and by getting the .deb directly. But everytime I get this error: 

> 
radu@radu-laptop:~$ sudo apt-get install xfce4-whiskermenu-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 xfce4-whiskermenu-plugin : Depends: libxfce4util4 (>= 4.3.99.2) but it is not installable
                            Depends: xfce4-panel (< 4.9) but 4.10.0-1ubuntu2 is to be installed
E: Unable to correct problems, you have held broken packages.


If I try to install libxfce4util4 I get the following error:
> 
radu@radu-laptop:~$ sudo apt-get install libxfce4util4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libxfce4util4 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libxfce4util-bin:i386 libxfce4util-common libxfce4util-bin


E: Package 'libxfce4util4' has no installation candidate


Apparently it was replaced by a set of other packages which I have already installed.

If this one cannot be installed, can anyone show me a similar menu? Thank you in advance.

Edit: I manager somehow to install Whiskermenu. It looks very nice, however I have one question: Can I add an image that is not a square format? Because any image I add, it's resized to 22px width, and I can't see the "Menu" text on it. I want something similar to this: [IMG]http://oi41.tinypic.com/9aveiq.jpg[/IMG]

---

