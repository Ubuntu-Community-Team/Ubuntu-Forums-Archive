---
title: "installing multiple GUIs, and switching between them!?"
date: 2014-07-09
forum: General Help
---

### Post by thexnightmare on 2014-07-09
Dear,
Any idea if i can install multiple GUIs like xde and lde on top of ubuntu and change between them?
Thanks

---

### Post by philinux on 2014-07-09
Yep then choose the session when you login.
They are DE's. Aka desktop environments.

---

### Post by thexnightmare on 2014-07-09
Any tutorial how to do that, as I am new to ubuntu and switching off from the windows OS

---

### Post by sudodus on 2014-07-09
You can do it, but it will clutter the menus and the disk with multiple programs for the same or similar purpose. And it is very hard to get it clean afterwards. So it might be good to have one production system, and one (or more) experimental system(s), dual boot or multiple boot. Then you can test many DEs in an experimental system.

Examples (the DE and the corresponding flavour)

```
sudo apt-get install lxde
sudo apt-get install lubuntu-core
sudo apt-get install lubuntu-desktop
sudo apt-get install xfce4
sudo apt-get install xubuntu-desktop
sudo apt-get install kde-full
sudo apt-get install kubuntu-desktop
...
```

Select 'session' alias DE by clicking on the round symbol in the log in screen

---

### Post by oldfred on 2014-07-09
Do you want the full Desktop Enviroment which includes all the default applications or just the gui or Windows Manager/WM or just the bare bones WM without its support tools (not suggested).

To see what you are running:
  fred@fred-Precise:~$  echo $DESKTOP_SESSION
gnome-fallback

      
 One users comparison of versions.
[http://mylinuxexplore.blogspot.in/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html](http://mylinuxexplore.blogspot.in/2012/04/ubuntu-1204-vs-xubuntu-1204-vs-kubuntu.html)

Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)

 Comparison of desktop environments - differences in software
[https://wiki.archlinux.org/index.php/Desktop_Environment](https://wiki.archlinux.org/index.php/Desktop_Environment)
[http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)
All Desktops in one:
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)
Both Unity and standard Gnome classic use Compiz as a WM, whereas Unity-2D and Gnome classic (no effects) use Metacity. 
Gnome shell and Cinnamon (which is a gnome-shell extension) use Mutter as a WM.

 
I prefer to install in another partition if testing a full meta-package which is the full install. Otherwise you get lots of packages with duplicate functionality. And you cannot easily uninstall a meta package. I have some applications from Kubuntu so want to keep those. 

 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
Or:
sudo apt-get install ubuntu-desktop

---

### Post by thexnightmare on 2014-07-09
Wow thanks for this amazing answer; Any idea on how to swithc a gui by terminal and not buy login screen?
And can u explain more this sentense as i am new?
1. [COLOR=#000000]but it will clutter the menus and the disk with multiple programs for the same or similar purpose. And it is very hard to get it clean afterwards[/COLOR]

---

### Post by thexnightmare on 2014-07-09
[oldfred]("http://ubuntuforums.org/member.php?u=852711")[COLOR=#000000]: Thanks, amazing response, I wlill read it again and again and get back to you[/COLOR]

---

### Post by sudodus on 2014-07-09
If you install several DEs to your only Ubuntu system, which you also want to use for daily tasks, your 'production system', you might come back to us ask how to remove all DEs except one, because it is 'cluttered' lots of programs. It is difficult to return back to a clean system, so it is better to do the testing in another installed system, a 'testing system' which is independent of the 'production system'.

---

### Post by HermanAB on 2014-07-09
In my experience, adding XFCE to an existing system is OK, since it is a sparse system. You do end up with a few more programs in the menu, but they are actually useful too.  However, adding KDE to a Gnome/Unity based system doesn't work so well - rather keep that one separate.

---

### Post by philinux on 2014-07-09
Xfce4 had very few dependencies.  Always a good idea to check those via synaptic.

---

### Post by monkeybrain20122 on 2014-07-09
You can, but it is a bad idea unless you have some compelling need (like remote desktop doesn't work with 3d desktop so need an alternative 2d desktop) and if you do install something like lxde would pull in less dependencies than xfce or god forbids, KDE.

P.S should just install lxde instead of lubuntu-desktop and xfce4 instead of xubuntu-desktop etc.

finally gnome-shell and Unity don't mix.

---

### Post by thexnightmare on 2014-07-09
Hello guys,
Firstthank you alot for your explanations, I was from couple of hour ZERO in ubuntu world and now I think I am oin the 


right direction.


After many tryout, researches, reads, with ubuntu adn linux world, i foud that ubuntu kernel have a top layer which 


called x window or tty, where tty is the erminals to control ubuntu and x window is a layer which have many Desktop 


Environments (DEs or GUIs) (like xfce, gnome, etc...), where you can control ubuntu kernel and utilities through DEs.


And there is a DEs manager u can install to control the Desktop Environments and select which one to login with, and 


ubuntu com with default app lightdm which contorl them, or you can install another one like gdm etc..., and:
1- You cant switch the DEs while you are logged in with a certain DEs, instead, you have to log out, then re login in 


another or same GUI.
2- DEs is just a layer or type of view the ubuntu and if you installed an app from a GUI u can access it from another 


GUI. (So its like themes in windows, from a certain point of view).
3- Each GUI can be installed as full dektop with default apps, or just the desktop view.


Am I right with what I said?


And I have few questions:
0- What do you mean by "cluttered" lots of program if install many DEs together?
1- What if I install a full desktop which have default apps, and the apps already exist, do they be installed 2 times, 


or they just skipped? so, in another wy, does the apps are shared or each DE have it's ow space and apps.
2- What if you installed 2 desktops which have intersections in default programs, and you uninstalled a desktop, does 


the common app removed?
3- After installing a DE which have default apps, do those apps appears in the other DE?
4- What is synaptic? do you mean ubuntu software center?
5- What are the differences between lxde, lubuntu-core, lubuntu-desktop?
6- Can I start specific DE from tty?
7- What I understood is the DE mean GUI + default apps, while GUI means just the GUI without default apps, am I right? if so, then what are the Windows Manager/WM or just the bare bones WM without its support tools? I think WM is something like a launcher or boot loader or light version of the DE or GUI, Right?

Thanks for your time

---

### Post by sudodus on 2014-07-10
> **thexnightmare said:**
> ...

And I have few questions:
0- What do you mean by "cluttered" lots of program if install many DEs together?

I try to explain again: Some or many programs are installed that perform the same or almost the same thing. It makes the menus (and dash) full with entries (icons) and it is harder to find what you want. But as described by at least two posts, XFCE is better than KDE in this respect.
> 

1- What if I install a full desktop which have default apps, and the apps already exist, do they be installed 2 times, 
No, exactly the same package will not be installed twice> 

or they just skipped? so, in another wy, does the apps are shared or each DE have it's ow space and apps.
2- What if you installed 2 desktops which have intersections in default programs, and you uninstalled a desktop, does 
the common app removed?

I'm not sure but it is hard to get back from a mixed system with two or more DEs to the original system with one DE (unless you restore from a backup).> 
3- After installing a DE which have default apps, do those apps appears in the other DE?
Yes, at least in some cases (according to my experience)> 
4- What is synaptic? do you mean ubuntu software center?

Synaptic is a front end to the install/update/upgrade program system. Software Center is another front end to the same program system. They can do the same or at least partially the same things. Many beginners prefer the Software Center while experienced users prefer Synaptic or running commands in a terminal window. I like Synaptic.
> 
5- What are the differences between lxde, lubuntu-core, lubuntu-desktop?

lxde - ultra light weight desktop environment
lubuntu-core - meta-package to install Lubuntu with only the central applications 'the core'
lubuntu-desktop - meta-package to install Lubuntu (the standard Lubuntu flavour)
> 
6- Can I start specific DE from tty?
Probably, but I don't know a good way to do it. You would have to remove the standard way of starting graphical desktop environments, for example booting into a text screen. Is this what you want, or do you want to start a new DE from within a running DE?
> 
7- What I understood is the DE mean GUI + default apps, while GUI means just the GUI without default apps, am I right? if so, then what are the Windows Manager/WM or just the bare bones WM without its support tools? I think WM is something like a launcher or boot loader or light version of the DE or GUI, Right?

Thanks for your time

In the bottom there is X-windows. A simple 'desktop GUI' is a Window Manager, WM, for example Openbox, that is used by LXDE to create a 'full desktop environment' with panels, wallpaper, menus etc.

In turn Lubuntu (lubuntu-desktop) uses and tweaks LXDE and adds application programs to make a complete Ubuntu flavour or linux distro with most things pre-installed for an average user. (You can log in to the Openbox session in Lubuntu, which can be a good option if you have low RAM or a slow CPU, and want to run an application, that will not run well in standard Lubuntu.)

And the other Ubuntu flavours are made the same way but using other building blocks.

---

### Post by thexnightmare on 2014-07-12
sudodus: I am extremely thankful, i just understand ed how things worked with ubuntu, it is great OS.

Concerning question 5:
Does DE package name (lxde) is the most general package which contains all meta packages like lxde-core, lxde-desktop, ...? or the lxde-desktop is the mot general package which contains everything? in another way, What is the difference between installing lxde,and installing lxde-desktop?

And about question 6:
a- I meant,of the linux dont have DE, and it is booting into text based system. and installed gnome or unity, how to launch it?
b- And how to modify the parameters of linux/ubuntu to allow choosing a Default DE aor text based once booted?
c- if i am in unity DE, and I go to tty, if i click ctrl+alt+f7 i go back to DE (same DE), can I go back to a different DE without logging out then logging in?

A new question:
- What are the differences between tty and terminal?

---

### Post by oldfred on 2014-07-12
I think most of differnces with DE and WM was explained in the links in post #5.
You do have to log out and log back in to change from one DE to another. The little gear/logo symbol in upper right corner is where you select DE.
[http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu](http://askubuntu.com/questions/64241/how-do-i-switch-to-xubuntu)

tty is for the very old teletype machine which was the terminal. 
[http://en.wikipedia.org/wiki/Teletype_Corporation](http://en.wikipedia.org/wiki/Teletype_Corporation)

When video monitors first appeared we called them glass teletypes.

---

### Post by sudodus on 2014-07-13
Please ***try*** the different options of windows managers and desktop environments! That way you will 'see' the differences in a much better way, than reading our explanations, or maybe I should say, trying it will help understand the explanations.

---

