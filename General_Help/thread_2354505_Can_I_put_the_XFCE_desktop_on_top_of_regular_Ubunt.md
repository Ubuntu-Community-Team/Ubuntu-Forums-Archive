---
title: "Can I put the XFCE desktop on top of regular Ubuntu"
date: 2017-03-03
forum: General Help
---

### Post by Phil Binner on 2017-03-03
I started using Ubuntu years ago, but have never got fully into it. I have always had at least 2 machines, however, and one of them has been some form of Linux. Regardless, I have always done serious work on Windows.  I would love to change that.

Until the Unity desktop was introduced I used regular Ubuntu, but I soon got fed-up of it's clumsy nature and went over to XUbuntu.  The desktop environment in XUbuntu is great, I run Cairo Dock for the launcher and have a disappearing panel at the bottom of the screen for notifications and open window switching, and finish up with something like a cross between Windows and a Mac which is faster, more friendly and more stable than either (possibly not more stable than a Mac, but very much friendlier, and way more stable than Windows 10).

The problem with XUbuntu is that it is limited, and it's internals are badly co-ordinated.  Whenever I need to get at the Settings I have to search all over, and finish up with not getting full information or control.  It doesn't include all the utilities, like the Disks program.  I searched for a way to install that but was unsuccessful.

So I have just come back to regular Ubuntu to give it another try, and I've been reminded of all the reasons I left. Mainly, the launch bar is like a clumsy dock, and I can't find a place to show all the running windows, like the panel in XUbuntu or the Windows quick start bar.  Worse, when I minimise a window Unity seems to forget what size it was.  When I'm working I tend to have windows side by side on the screen, sized to fill the screen. I may have a spreadsheet, a text document, several instances of a file browser set to different locations, and an internet application, like my bank, open at the same time.  Flicking between them in Unity is virtually impossible with any kind of grace.

So what I'm hoping I can have is the XFCE desktop, and only the desktop, imposed of top of the full Ubuntu instead of Unity. Can this be done, or do I have to stay with Windows a bit longer.

---

### Post by ajgreeny on 2017-03-03
I've been using Xubuntu for several years and find it the best of the *ubuntu family, but I do not see the problem of managing the settings that you seem to have.

I use an auto-hidden panel on the left side of my screen with many launchers in it.  One of those is for the **Settings Manager** which you have maybe not found, but which gives easy access to all settings similar to that in Ubuntu's **System-Settings**.

Give that a try and see if you can not fall in love with Xubuntu again, rather than add another desktop to Ubuntu with unity which you find clumsy.

See my screenshot for what I can see from a single click on the left panel.

---

### Post by Phil Binner on 2017-03-03
You're probably right. I also use the auto hidden panel, but at the bottom of the screen. I find XUbuntu very friendly, it's just that recently I've been running into things I can't do easily.  Perhaps it's just that I don't understand it well enough. 

I'm hoping no to put a new desktop beside Unity, I'm hoping to replace unity. XFCE is what I'm hoping to replace it with.

---

### Post by vasa1 on 2017-03-03
> **Phil Binner said:**
> ... It doesn't include all the utilities, like the Disks program.  I searched for a way to install that but was unsuccessful.
...The package is *gnome-disk-utility*, the terminal command to launch it is *gnome-disks*, and the desktop file is named *Disks*.

---

### Post by Phil Binner on 2017-03-03
Is it actually possible to replace Unity with XFCE.  If it is, would that be in any way different from XUbuntu.

---

### Post by HermanAB on 2017-03-03
apt install xfce
log out
select xfce desktop
log in

---

### Post by yetimon_64 on 2017-03-03
> apt install xfce**4**
log out
select xfce desktop
log in

@ OP, if you try HermanAB's code try it with "xfce**4**". Or if you want all of the xubuntu applications as well; change "xfce4" to "xubuntu-desktop" (depends on what xfce style of set up you want).

> **Phil Binner said:**
> Is it actually possible to replace Unity with XFCE...

HermanAB's post will give you the option of an xfce4 desktop session very easily. Once you log into the xfce session that session will become your standard log in until changed again at the log in screen. The power cog icon on the user name entry box of the log in screen is where you can select which session to use. I actually have the choice of Ubuntu (using Unity), xubuntu (using xfce4), gnome3, cairo-dock and ubuntu-studio (another session option that uses an xfce4 desktop). You can run many parallel desktop sessions on a standard Ubuntu base choosing whichever you like at the log in screen.

> **Phil Binner said:**
> ...  If it is, would that be in any way different from XUbuntu.
The xfce4 option that is installed with HermanAB's code will give a plain/vanilla desktop set up without any of the standard xubuntu applications. To get the full set of xubuntu applications you would need to choose the xubuntu-desktop package instead.

Regards, yeti.

---

### Post by oldos2er on 2017-03-03
> The problem with XUbuntu is that it is limited, and it's internals are badly co-ordinated. I'm not sure I understand what you mean here. If I need to open the Settings Manager, I either right-click on the desktop and select it from the menu, or hit the Windows key to open the whisker menu and type in "settings." Do you have the whisker menu enabled? It's incredibly useful, I find. 

Naturally Xubuntu does not include many of the gnome-based apps that are included by default in Ubuntu; this is by design. I'm not sure how you "searched for a way to install that" but I would run a command like ```
apt search disk utility
``` which produces a lot of output, but in that list you'll find gnome-disk-utility. If you prefer GUI package management, try Synaptic package manager, if you haven't already. It is less buggy, and superior to Software Center, in my opinion.

---

### Post by ajgreeny on 2017-03-03
> **oldos2er said:**
> I'm not sure I understand what you mean here. If I need to open the Settings Manager, I either right-click on the desktop and select it from the menu, or hit the Windows key to open the whisker menu and type in "settings." Do you have the whisker menu enabled? It's incredibly useful, I find. 

Naturally Xubuntu does not include many of the gnome-based apps that are included by default in Ubuntu; this is by design. I'm not sure how you "searched for a way to install that" but I would run a command like ```
apt search disk utility
``` which produces a lot of output, but in that list you'll find gnome-disk-utility. If you prefer GUI package management, try Synaptic package manager, if you haven't already. It is less buggy, and superior to Software Center, in my opinion.
^^^^+1
The settings manager was the one thing you spoke of before that you could not find, which is why I added my screenshot.
What else is missing that you want and can not find? Disks is installed by default in Xubuntu 16.04 and is called just that, Disks, so should have been found in whisker menu with a search of "disk".

---

### Post by Phil Binner on 2017-03-07
Thanks to all of you.  I now have Ubuntu running with a choice of desktops - Unity, XFCE and Cairo Dock.  In the main this is just what I want, with a couple of exceptions.

First settings.  I put the unity System Settings button into the Cairo Dock before I changed to XFCE, but now if I use it I get a window that looks like the screenshot from ajgreeny but only contains 3 items, Language Support, Printers and Software & Updates. (sorry, I tried to paste a screenshot here but all I achieved was to paste a link to my pictures folder.)  When I select the Settings editor in the Whiskers menu I get an entirely different window, concerned with settings for Thunar, etc.  I can't find anything in Whiskers called a Settings Manager.  I would like to sort this one.

The other thing is that Cairo Dock does not load at startup, as it used to when running XUbuntu. Do I have to do something else to achieve this.

PS I know it's not really part of this thread, but If someone can tell me how to paste a screenshot in a post it would help me to provide you with better information

---

### Post by vasa1 on 2017-03-07
> **Phil Binner said:**
> ...

PS I know it's not really part of this thread, but If someone can tell me how to paste a screenshot in a post it would help me to provide you with better information
Click on the paperclip icon just above the posting (text box) area. You'll get a window enabling you to point to the image you want to upload. Then just click upload and close that window when you're done!

---

### Post by Phil Binner on 2017-03-07
Apologies to oldos2er.  I just re-read your post and realised I hadn't been reading it correctly.  I thought I had been doing that, but I hadn't.  I now have settings.  I just need to solve loading Cairo Dock at startup, and that is not such an important issue.

---

### Post by adedamoo-ab on 2017-03-07
Do you have the desktop feel you wanted now.
You can use Xubuntu and build it up to meet your need.

---

### Post by Phil Binner on 2017-03-07
OK. I was looking at it and not seeing it.  Thanks for your help.

---

### Post by Phil Binner on 2017-03-07
I was looking at this but not seeing it.  Sorry.  How do I mark this as solved.

---

### Post by Phil Binner on 2017-03-07
Yes I do.  I have also learned enough about XUbuntu to go back there and try to do as you suggest.  What I am doing is to build a media machine with 5.1 sound output, so I think there will be other questions as I go on, but for now I am happy.

---

### Post by yetimon_64 on 2017-03-07
> **Phil Binner said:**
> ... How do I mark this as solved.
The blue link in the middle of my signature has a guide on how to mark your thread as solved. Cheers, yeti.

---

