---
title: "Newbie To Linux and in need of help."
date: 2008-05-19
forum: General Help
---

### Post by AmenX on 2008-05-19
Hi everyone.

I've heard many good things about Linux and Ubuntu, so I decided to take a pause off windows and try this out.
But, I have some questions that need to be answered before I can do so.


1.I've heard that there is a way to install Ubuntu, without burning a disk and that you can install it from your desktop. Is that true? If so how?

2. What is some 'must have' software I can download for Ubuntu? Or in general, where can I download some? 

3. This is going to sound stupid, but is Ubuntu/Linux really the godly OS people make it out to be, or is that just fanboyism? I don't doubt them, but I'd just like to know.


Thank you all very much for your help, I cannot wait to join the Unbuntu community as soon as possible.

---

### Post by knutschr on 2008-05-19
Go to [http://wubi-installer.org/](http://wubi-installer.org/)
There you can install Ubuntu as just another program in Windows, from the net.
You have found this place!
Therefor I think you will easily find answers to your other questions.

I hope you will join the freedom and safety of Linux!

---

### Post by UnWarierMage224 on 2008-05-19
There is an option in ubuntu to install it within your windows installation. WUBI, I think it is called. That's if you want to test-drive ubuntu. 

Installing software is done through add/remove programs in the applications menu in ubuntu. also done through synaptic package manager. Beauty of ubuntu is there's lots of stuff for it online... but it comes pretty decently loaded too. 

As for question #3, I prefer Ubuntu to XP but I have XP still on my  computer because there's a few XP programs I like and use. 

Best, 

-'Mage

---

### Post by AmenX on 2008-05-19
I'm downloading Ubuntu right now, and then in 20 minutes when it's done I'll install Wubi ((Thanks for the link.)) And install it that way.

I have noticed one this about Linux over Windows.
Everything looks so..Clean.
I mean, I keep my desktop pretty clean as it is right now, but for some reason Linux looks shiny.

I have a few more questions as well.


1.Will Wubi help me partition my drives? Or does the installation it's self help me with that? I saw screenshots of a menu coming up and asking so..I'm not sure.

2. What is a good website to get some software? Free of course.

---

### Post by knutschr on 2008-05-19
Wubi installs Ubuntu In your Windows partition.

When you have installed, restarted and chosen Ubuntu in your now dual boot,
write in terminal:
gksu synaptic
There, open all repositories an reread them.
Then you have 15-20.000 free programs to choose from! 

(Most people, I think also draw the toolbar to the bottom, as eyer eyes are made to look down)

---

### Post by AmenX on 2008-05-19
In my mind I was thinking "AHH This all seems counfusing!" But then I noticed something.
Obviously a new OS will not be like XP.
It will be just like getting used to XP for the first time, so..hopefully I'll learn fast.

Two more minutes until it's done downloading, then I'll come back here and maybe ask a few more things.


The one thing I need know now is..

How do I make it boot in Ubuntu? Will it ask me at start up, or will I have to go through something harder?

---

### Post by knutschr on 2008-05-19
Yo will be asked during startup, yes:-)

---

### Post by AmenX on 2008-05-19
I already like this community, everyone is very helpful.

Well..Time to go try my luck on installing this thing.

Wish me luck and please check back here every so often.


Thank you so much for your help so far.

---

### Post by AmenX on 2008-05-19
Well, I have a problem. :(

I burned it to a CD.

The Ubuntu logo came up and asked me what I wanted to do.
I chose "Install Ubuntu from cd' Or whatever that is.
And then it gave me a boot disk reading error.

---

### Post by knutschr on 2008-05-19
Well.
So you have chosen to install in a new directory, instead og using wubi?
Agree that is better, as the new partition will be formatted as ext2, that is far better than NTFS.
It is a little bit more difficult, though, but it seems like you will make it.

Try burning again, and slower.

---

### Post by AmenX on 2008-05-19
I only burned it at 12x though. :(
Rather ironically to what you said, I've already completed loading it on Wubi and now it wants me to restart.

---

### Post by knutschr on 2008-05-19
Then do it, and wait for the rest of the installation to finish.
I have no experience with wubi.
It seems to be OK, after what I read.
You can change later, you know :-)

---

### Post by AmenX on 2008-05-19
I've installed it and I'm using it right now.
I have to admit, so far it's great.
THe layout and how everything works anyways.
I love how you can have two different 'workstations' that's just so cool I don't even know how to explain it.

I'm downloading Linux video card drivers right now, so I'm hoping they'll work. GOing to install them the second I make this post.


I know I could use google, but you guys would know much better/safer places than I could find.


WHere can I download some software and addons or well..what ever you want to call it.
WHat's the best site to get it from?

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> I've installed it and I'm using it right now.
I have to admit, so far it's great.
THe layout and how everything works anyways.
I love how you can have two different 'workstations' that's just so cool I don't even know how to explain it.

You can have 3, 4, 5... you can even arrange them on a rotating, translucent 3D cube (though I'm not sure what that's good for, exactly)

> I'm downloading Linux video card drivers right now, so I'm hoping they'll work. GOing to install them the second I make this post.


I know I could use google, but you guys would know much better/safer places than I could find.


WHere can I download some software and addons or well..what ever you want to call it.
WHat's the best site to get it from?

You could always surf sourceforge.net or various projects' homepages, and figure out how to build stuff from source (unless they have ready-made .deb packages for your Ubuntu version). 

Sometimes, that actually works :). 

You can usually let Ubuntu download and install software semi-automatically, though - by running a program called a *package manager* that connects to online *repositories* of vast amounts of Ubuntu-ready software. This is where you get upgrades as well as new stuff. 

(I'm assuming you use Ubuntu's default desktop, GNOME.)

One (very much simplified) package manager is the "Add/Remove" tool in GNOME's "Applications" menu (in the menu bar at the top of the desktop). You can browse through the categories on the left, or use the search field. Tick whatever you want, then "Apply Changes" - voila!

With the "Preferences" button and "Show:" drop-down list, you can control which repositories (software sources) you can install from, and which of their packages will be displayed. (Not everything is activated from the start.)

Anyway, "Add/Remove Applications" can't get you everything that's available from the repositories - it's mostly stuff that beginners can identify (i.e. "Thunderbird" yes, "libncurses5-dev" no... "MAME" yes, "apache2-mpm-prefork" no). 

For full access to the repositories, you can use "Synaptic" (GNOME) (or "Adept" (KDE)). Synaptic is in the "System" menu under "Administration". You can activate/deactivate (and add!) repositories through Synaptic's "Settings" menu.

Here's a more comprehensive guide that you could read!
[https://help.ubuntu.com/8.04/add-applications/C/index.html](https://help.ubuntu.com/8.04/add-applications/C/index.html)

---

### Post by knutschr on 2008-05-19
The best is to download and install from the repositories, using synaptic.
You have activated all?
Be satisfied with 15-20.000 free programs for the moment :-)

---

### Post by AmenX on 2008-05-19
I've brought up Synapatic and installed a gamma manager which I need since my monitor is dark and I need to manually change it ((That's what I did on XP.))

But, after it's installed I Hoenstly have no idea how to get to the program.
I've looked everywhere I can think of, but I don't know where Synaptic puts it.

---

### Post by quinnten83 on 2008-05-19
Hi AmenX,
read the following link to understand how software installation work in Ubuntu and in Linux.
If you still need to find software try [www.getdeb.net](www.getdeb.net).
It contains .deb files which you can just double click and it will be installed.

---

### Post by knutschr on 2008-05-19
A very good and also funny story of Linux is here:
[http://www.desktoplinux.com/articles/AT7702650846.html](http://www.desktoplinux.com/articles/AT7702650846.html)

---

### Post by AmenX on 2008-05-19
I'll have to read that later because of how long it is.

BUt, do you happen to know how I can find the files I installed off of Synaptic? WHat folder they are in or something like that?

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> I've brought up Synapatic and installed a gamma manager which I need since my monitor is dark and I need to manually change it ((That's what I did on XP.))

But, after it's installed I Hoenstly have no idea how to get to the program.
I've looked everywhere I can think of, but I don't know where Synaptic puts it.

What was the name of the package? 

Most stuff is automatically added to the Apps menu, but command line programs usually aren't (starting them from a menu doesn't usually make much sense anyway). 

You can find out what files were installed by right-clicking the package in Synaptic, then "Properties". Or set up Synaptic so that it displays the properties at all times (good idea IMO).

There are no (or very few) program-specific folders in Linux so that's a big difference to Windows. Instead, executable files (programs themselves) usually go into one of the bin(aries) directories: /bin, /usr/bin, /usr/local/bin among others. That also means they're automatically in your path and you can run them by typing their name at a command prompt or in a Run dialogue.

---

### Post by AmenX on 2008-05-19
> **mrowth said:**
> What was the name of the package? 

Most stuff is automatically added to the Apps menu, but command line programs usually aren't (starting them from a menu doesn't usually make much sense anyway). 

You can find out what files were installed by right-clicking the package in Synaptic, then "Properties". Or set up Synaptic so that it displays the properties at all times (good idea IMO)


kgamma

THat's what it's called.

I right clicked and went to properties, but it didn't say anything about where it's at.

---

### Post by quinnten83 on 2008-05-19
AmenX,
you're applying windows work logic to understand Ubuntu, that is not going to work here. This is really completely different.

---

### Post by AmenX on 2008-05-19
Oh wait, I thought you said "YOu can right click it and choose properties to see where the files were installed to."

Not "What files were installed"

I Misread that.

---

### Post by mrowth on 2008-05-19
Ah... the description says: "KGamma is a KDE Control Center module for gamma calibration/correction of XFree86." KDE is a desktop environment like GNOME. Only different. If you're not running KDE, you may want to install something that wasn't meant to integrate with it. 

> **AmenX said:**
> kgamma

That's what it's called.

I right clicked and went to properties, but it didn't say anything about where it's at.

You'll have to go to the "Installed Files" tab of the Properties window. 

Here's what it'll say:

/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/kgamma
/usr/share/doc/kgamma/copyright
/usr/share/doc/kgamma/changelog.gz
/usr/share/doc/kgamma/changelog.Debian.gz
/usr/share/doc/kde
/usr/share/doc/kde/HTML
/usr/share/doc/kde/HTML/en
/usr/share/doc/kde/HTML/en/kgamma
/usr/share/doc/kde/HTML/en/kgamma/index.cache.bz2
/usr/share/doc/kde/HTML/en/kgamma/index.docbook
/usr/share/applications
/usr/share/applications/kde
/usr/share/applications/kde/kgamma.desktop
/usr/share/apps
/usr/share/apps/kgamma
/usr/share/apps/kgamma/pics
/usr/share/apps/kgamma/pics/background.png
/usr/share/apps/kgamma/pics/cmyscale.png
/usr/share/apps/kgamma/pics/darkgrey.png
/usr/share/apps/kgamma/pics/greyscale.png
/usr/share/apps/kgamma/pics/lightgrey.png
/usr/share/apps/kgamma/pics/midgrey.png
/usr/share/apps/kgamma/pics/rgbscale.png
/usr/share/icons
/usr/share/icons/hicolor
/usr/share/icons/hicolor/16x16
/usr/share/icons/hicolor/16x16/apps
/usr/share/icons/hicolor/16x16/apps/kgamma.png
/usr/share/icons/hicolor/32x32
/usr/share/icons/hicolor/32x32/apps
/usr/share/icons/hicolor/32x32/apps/kgamma.png
/usr/share/icons/hicolor/48x48
/usr/share/icons/hicolor/48x48/apps
/usr/share/icons/hicolor/48x48/apps/kgamma.png
/usr/bin
**/usr/bin/xf86gammacfg**
/usr/lib
/usr/lib/kde3
/usr/lib/kde3/kcm_kgamma.la
/usr/lib/kde3/kcm_kgamma.so
/usr/share/doc/kde/HTML/en/kgamma/common

I highlighted the file in the /usr/bin directory because it's the executables that go into bin directories. You can run xf86gammacfg from any command line (terminal/console), even if you don't use KDE. (I dunno how to use xf86gammacfg, though.)

Maybe GNOME has gamma correction already? Check out it's Settings thingie, whatever it's called. 

If you have an NVIDIA card with the "official" (non-free, restricted) drivers, you can set gamma with the nvidia-settings tool.

---

### Post by knutschr on 2008-05-19
In terminal:
whereis [name of program]
If you are in doubt, you can also type whoami :-)

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> Oh wait, I thought you said "YOu can right click it and choose properties to see where the files were installed to."

Not "What files were installed"

I Misread that.
It tells you both what and where. 

You don't really have to know where it is, though. 

Linux knows better than you where to look for its own executables - for example, to run Firefox, you can type "firefox" (at a command line or Run dialogue) without knowing where exactly the files are. 

Also, most programs are automatically added to the Applications menu. 

This one may not be if it's not something a GNOME user can run by clicking on it. 

> **knutschr said:**
> In terminal:
whereis [name of program]
That's a good tip, but it doesn't help in this case, because the executable isn't called kgamma. It's called xf86gammacfg.

---

### Post by AmenX on 2008-05-19
Based in the small bit I've learned about the terminal thing, and Syndapic I've figured out that there is something called "xgamma" on here that goes along with something called "X server utilities"

But sadly, once again I don't know how to bring it up. I did the "whereis xgamma" to try and figure it out, then typed in what it said to see if it would run the program or what ever it's supposed to do but.. It didn't.

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> Based in the small bit I've learned about the terminal thing, and Syndapic I've figured out that there is something called "xgamma" on here that goes along with something called "X server utilities"

But sadly, once again I don't know how to bring it up. I did the "whereis xgamma" to try and figure it out, then typed in what it said to see if it would run the program or what ever it's supposed to do but.. It didn't.

It does when I type it. Looks like this:

```
mrowth@mycomputer:~$ xgamma
-> Red  1.000, Green  1.000, Blue  1.000
```

(Again, you don't have to "whereis" it first. You can just type "xgamma", not "/usr/bin/xgamma".)

---

### Post by AmenX on 2008-05-19
> **mrowth said:**
> It does when I type it. Looks like this:

```
mrowth@mycomputer:~$ xgamma
-> Red  1.000, Green  1.000, Blue  1.000
```

(Again, you don't have to "whereis" it first. You can just type "xgamma", not "/usr/bin/xgamma".)

Yeah, that's exactly how it looks.

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> Yeah, that's exactly how it looks.

Those are the current gamma values. You can set new ones. For example by typing: 
xgamma -gamma 1.4 

Or if you just want to increase gamma of green and blue:
xgamma -ggamma 1.2 -bgamma 1.2

For more instructions, use the man command (manual):
man xgamma

---

### Post by AmenX on 2008-05-19
Darn, I got that to work but when I set my Gamma higher it makes certain things lose color.
I need to find a program that will let me use contrast, gamma, brightness.

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> Darn, I got that to work but when I set my Gamma higher it makes certain things lose color.
I need to find a program that will let me use contrast, gamma, brightness.
Sorry, can't help you there, unless you have an NVidia card or want to install KDE.

---

### Post by AmenX on 2008-05-19
YOu cna change stuff with the ATI tool thing as well, but when I try to install it I get an error.

WOuld I Just look up KDE in Synaptic or on google, or?

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> YOu cna change stuff with the ATI tool thing as well, but when I try to install it I get an error.
What error? Not that I know ATI tools, have always made sure to buy Nvidia for Linux...

> WOuld I Just look up KDE in Synaptic or on google, or?

KDE and KDE apps are available through Synaptic. 

Maybe you could try installing just the KDE Control Center; the package is called "kcontrol". 

Else - KDE is a complete desktop environment, will take a couple minutes to install. KDE should be either the "kde" package, or if you want a more KDE-ified overall look'n'feel, the "kubuntu-desktop" package (like, matching boot splash screens and stuff... I don't know if it installs more apps too or what). 

You'll still be able to use GNOME, of course - you can select which through one of the menus on the login screen. You can use GNOME apps in KDE, and KDE apps in GNOME. (Some good KDE apps are: K3B (CD/DVD-burning), Amarok (music player), Kaffeine or SMPlayer (video/DVD player), Kate (KDE Advanced Text Eitor), Kmail (email), Knode (Usenet), Krita (graphics editor), Gwenview (graphics viewer)... many of them are installed by default along with KDE.)

---

### Post by AmenX on 2008-05-19
Wow, that sure did add a lot of stuff.
I installed the theme thingy too, but I can't find it when I go to appearence? How do I get it to work?

Now I think all I have to do is reinstall that Kgamma thing.

---

### Post by mrowth on 2008-05-19
> **AmenX said:**
> Wow, that sure did add a lot of stuff.
I installed the theme thingy too, but I can't find it when I go to appearence? How do I get it to work?
Dunno, "theme thingy" is a bit vague ;). All that stuff should be under Appearance & Themes in the Control Center (and the Settings menu)

> Now I think all I have to do is reinstall that Kgamma thing.

Personally I don't notice a difference; there's always a Color & Gamma tab under Peripherals -> Monitor & Display - whether or not I've installed kgamma.

Uh... still no contrast/brightness there... it probably does the exact same thing as xgamma. What the KDE Control Center can do here isn't KDE-specific at all; it can (in Administrator Mode) modify  the X config file, /etc/X11/xorg.conf -- adding a line like "Gamma 1.21 1.19 1.21" to Section "Monitor". That's valid whether or not you run KDE.

---

### Post by knutschr on 2008-05-20
I use my monitor's in-built configuration tool to adjust brightness, gamma, contrast asw, with the buttons under the screen.
I think that is better than using software in the OS.

---

### Post by knutschr on 2008-05-20
> **AmenX said:**
> Wow, that sure did add a lot of stuff.
I installed the theme thingy too, but I can't find it when I go to appearence? How do I get it to work?


You choose KDE (Kubuntu) by choosing under Sessions in log-in screen.
You will, however, be able to use all the programs from both Gnome and KDE.

---

