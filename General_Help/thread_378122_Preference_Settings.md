---
title: "Preference Settings"
date: 2007-03-06
forum: General Help
---

### Post by n8oay on 2007-03-06
I just started using Linux a few weeks ago, and installed Ubuntu 6.10 a couple days ago, and I like it well enough that I ordered the "Ubuntu Linux Bible" from Amazon. I have several newbie-type questions, but will wait until the book I ordered from Amazon comes for most of them, but I have a few things that I am finding a bit irritating right now...

1 - I am finding that some windows remember the location and size, while others do not. Is there a way to force all windows to remember where I move them to?

2 - I have been able to add several application buttons to the panel, but can not figure out how to add a Nautilus button.

3 - When I change the wallpaper, it changes for both desktops. Is there a way to use different backgrounds on each desktop?

Thanks for the help. I am sure that I will be back for more...

---

### Post by FIONEX on 2007-03-06
3.  The thing about linux is that it's open source and it's all configuration based on text files and the like.  Everything can be changed from the source and recompiled.  So with a little bit of editing, I'm sure you can make your desktop do whatever you want it to do.  However, the feature you're asking for (each desktop have a different wallpaper), I don't think that's implemented in the GUI.  I don't know if you can just change the config files to get it either.  It's probably something you'll have to program into it yourself.

2.  Type 'nautilus --help' into a terminal and see the options it has.  Then add an application launcher to your panel and make it run the comman "nautilus --no-desktop" or whatever the option is to not have a desktop.  I don't use nautilus, so I wouldn't know.

1.  I've never experienced this in gnome.  But maximized windows will remember their position before you maximized them.  I use XFCE, not gnome, and I find it to be much faster and suites my preferences.

I hope this ramble helps a bit!

---

### Post by K.Mandla on 2007-03-06
> **n8oay said:**
> 1 - I am finding that some windows remember the location and size, while others do not. Is there a way to force all windows to remember where I move them to?
There's an application called devilspie that, if I understand it right, will intercept windows as they open and force them into certain locations. For windows that don't remember where they were opened, that might be an option for you. But I have to admit I've never used it, only read about it.

> **n8oay said:**
> 2 - I have been able to add several application buttons to the panel, but can not figure out how to add a Nautilus button.
The *nautilus --no-desktop* command should do the trick, like FIONEX mentioned.

> **n8oay said:**
> 3 - When I change the wallpaper, it changes for both desktops. Is there a way to use different backgrounds on each desktop?
I think that's an option in KDE, but not in Gnome. If you search around the forums a bit, someone might have come up with a solution for Ubuntu, but I'm not aware of one.

Have fun!

---

### Post by Arisna on 2007-03-06
All of these things can easily be done in KDE.  If you tend to like configuring things such as this extensively, KDE might be a good fit for you.  If you want, you can try it out easily by installing the kubuntu-desktop package.  It is generally advisable to use the command line package manager aptitude instead of Synaptic for this, because it makes uninstalling the whole KDE package easier later if you decide you don't want it.  Here's how to do it:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```

You can then choose KDE when you log into your machine.

If you don't like KDE, you can get rid of it by running

```
sudo aptitude remove kubuntu-desktop
```

Credit goes to aysiu for spreading this process around the forums!

Edit:  The only thing on your list whose process isn't obvious in KDE is the first one.  You get to it through Right Click on Title Bar > Configure Window Behavior.

---

### Post by n8oay on 2007-03-06
None of the options that I found running 'nautilus --help' worked. Every option adds a button that will only Lock the Desktop. Just since I posted my message, I have decided to go to Linux App Finder and look for something better...

> **FIONEX said:**
> 2.  Type 'nautilus --help' into a terminal and see the options it has.  Then add an application launcher to your panel and make it run the comman "nautilus --no-desktop" or whatever the option is to not have a desktop.  I don't use nautilus, so I wouldn't know.


---

### Post by LenzM on 2007-03-06
Just go to Applications -> Accessories and drag the 'File Browser' on to the panel.

---

### Post by n8oay on 2007-03-06
I tried Kubuntu before I installed Ubuntu, and did not like it mostly due to Konqueror. I may decide to revisit Kubuntu and try a different file manager (I am already dual booting with Xandros, and have a lot of available hard drive space). Other than GNOME vs KDE, are there any other differences between Ubuntu and Kubuntu? I have DVDs of both.  I may try Xfce too...once I learn my way around a bit better. I have been using Windows since version 3.1, and definitely like to configure preferences. I decinded a long time ago that Vista will never touch my hard drive, and I think it is long overdue for me to switch to Linux to get away from the security hassles.
 
> **Arisna said:**
> All of these things can easily be done in KDE.  If you tend to like configuring things such as this extensively, KDE might be a good fit for you.  If you want, you can try it out easily by installing the kubuntu-desktop package.  It is generally advisable to use the command line package manager aptitude instead of Synaptic for this, because it makes uninstalling the whole KDE package easier later if you decide you don't want it.  Here's how to do it:

---

### Post by n8oay on 2007-03-06
I do not see 'File Browser" anywhere on the Application or Places menus. Gnome Commander is downloading right now...

> **LenzM said:**
> Just go to Applications -> Accessories and drag the 'File Browser' on to the panel.

---

### Post by ramjet_1953 on 2007-03-07
To add a Nautilus File Manager button, just click on Applications>Accessories and then drag the File Browser icon to the panel.

Regards,
Roger :cool:

---

### Post by Arisna on 2007-03-07
> **n8oay said:**
> I tried Kubuntu before I installed Ubuntu, and did not like it mostly due to Konqueror. I may decide to revisit Kubuntu and try a different file manager (I am already dual booting with Xandros, and have a lot of available hard drive space). Other than GNOME vs KDE, are there any other differences between Ubuntu and Kubuntu? I have DVDs of both.  I may try Xfce too...once I learn my way around a bit better. I have been using Windows since version 3.1, and definitely like to configure preferences. I decinded a long time ago that Vista will never touch my hard drive, and I think it is long overdue for me to switch to Linux to get away from the security hassles.

Other than GNOME vs. KDE, there is essentially no difference at all between Ubuntu and Kubuntu.  You can even install the Kubuntu environment right alongside regular Ubuntu in the same installation, as I described before.

Also, if you don't like Konqueror, there are a couple of other good KDE file managers.  First, there is Dolphin, which somewhat resembles Nautilus, and second, Krusader, which is a twin-pane file manager that I have taken a real liking to lately. :)

If you try XFCE, you may also like Thunar, which is the default file manager in Xubuntu.  It is closer to Nautilus than to Konqueror.  I kind of liked it when I used Xubuntu a few months ago.

---

### Post by n8oay on 2007-03-07
Thanks for the assist! I have KDE running now, and I figured out how to get to GNOME if I want it by changing sessions at login.:)  

I may try Xfce later...next task is to dump Konqueror, then get the email set up. For that task, I have a Versora Progression CD that came with the retail box set of Xandros 4, which I am probably going to nuke. The retail box with the printed docs has been a great learning tool, but once I got into actually using Xandros, I found it to be a bit too much dumbed down. 



> **Arisna said:**
> All of these things can easily be done in KDE.  If you tend to like configuring things such as this extensively, KDE might be a good fit for you.  If you want, you can try it out easily by installing the kubuntu-desktop package.  It is generally advisable to use the command line package manager aptitude instead of Synaptic for this, because it makes uninstalling the whole KDE package easier later if you decide you don't want it.  Here's how to do it:

```
sudo aptitude update
sudo aptitude install kubuntu-desktop
```



---

