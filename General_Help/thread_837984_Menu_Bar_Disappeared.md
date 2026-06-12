---
title: "Menu Bar Disappeared"
date: 2008-06-23
forum: General Help
---

### Post by user1nachi on 2008-06-23
I just upgraded from Ubuntu 7.10 to 8.04 (both defaults, standard, I don't know much other information). After restarting, as it said was required, I found that the entire menu bar (the whole thing, so no option to shut down, no administration, no firefox link, etc) is gone. I don't know what happened or how to get it. 

I opened up firefox by double clicking on an icon on the desktop that was in open office spreadsheet, typed in [www.google.com](www.google.com) and clicked on it. 

I looked around and saw a few things saying try alt -f2, but that did nothing. If anyone knows how to fix this, please let me know. Thank you.

---

### Post by kripkenstein on 2008-06-23
Hmm, it sounds like your panels got 'broken' somehow during the upgrade.

Can you open a terminal and try to run 'gnome-panel'?

---

### Post by user1nachi on 2008-06-23
I thought about trying to open a terminal and try to find a command to place the menu bar, but the only way I know of accessing the terminal is to find it on the menu bar under applications. I suppose I could search around the folders in the hard drive and find it there, but that seems like more trouble than it's worth while I still don't have any solid plan of using the terminal.

Do you know the actual commands I would type in to do this?

---

### Post by kripkenstein on 2008-06-23
First let's make sure we are talking about the same thing. Menus are the things that are on the top part of windows, with File/Edit etc., and 'panels' are the things that sit on the desktop and have the main menu, shutdown button, launcher for Firefox, etc.

Based on your description, I think the problem is the panels are missing?

If so, then my suggestion is to run gnome-panel on the commandline and see if that gives errors. You can open a terminal by running gnome-terminal (should be in /usr/bin, if I remember correctly), if you can somehow browse to it.

Otherwise, you can try to go to a fullscreen terminal with control-alt-F1, then run gnome-panel in there. To get back, control-alt-F5 (or 6, or 7 - I forget) will return the graphical mode.

---

### Post by misho1721 on 2008-06-23
You mentioned searching around for terminal on the drive, so you have access to a file manager?

I found my terminal executable in "/usr/bin" the default is called gnome-terminal

Something similar happened to me I uninstalled evolution and clicked through the dependencies, upon reboot I found that gnome-panel had been uninstalled too

---

### Post by user1nachi on 2008-06-23
Thank you both for your help, I appear to be getting somewhere.

The panels are what is missing, I'm sorry; I was unaware that that was the terminology used.

I opened up the full screen terminal, and ran gnome-terminal and it said, "cannot open display:"
Run run help etc....

I also managed to open one folder on my desktop and find the regular terminal. I ran gnome-display there and it said, "Segmentation fault"

I also went to the help and it has an application option for what seems to be a display mode. The following is copy pasted from the terminal, viewing the final option given under gnome-panel --help:

Application Options:
  --display=DISPLAY              X display to use

user1@user1-laptop:/usr/bin$ gnome-panel --display=DISPLAY
cannot open display: DISPLAY
Run 'gnome-panel --help' to see a full list of available command line options.


My understanding now is that it's a problem in the gnome-panel app, so I guess I should try to install it. I'll try to just do a app get or something.

---

### Post by kripkenstein on 2008-06-23
> **user1nachi said:**
> Thank you both for your help, I appear to be getting somewhere.

The panels are what is missing, I'm sorry; I was unaware that that was the terminology used.

I opened up the full screen terminal, and ran gnome-terminal and it said, "cannot open display:"
Run run help etc....

I also managed to open one folder on my desktop and find the regular terminal. I ran gnome-display there and it said, "Segmentation fault"

I also went to the help and it has an application option for what seems to be a display mode. The following is copy pasted from the terminal, viewing the final option given under gnome-panel --help:

Application Options:
  --display=DISPLAY              X display to use

user1@user1-laptop:/usr/bin$ gnome-panel --display=DISPLAY
cannot open display: DISPLAY
Run 'gnome-panel --help' to see a full list of available command line options.


My understanding now is that it's a problem in the gnome-panel app, so I guess I should try to install it. I'll try to just do a app get or something.
I'm not sure, but I think DISPLAY should be the display number, typically 0 or 1 (or :0 or :1, I seem to remember).

However, if gnome-display crashes, that's not a good sign. You can try to reinstall gnome-display (and gnome-panel), and see if that helps.

---

### Post by user1nachi on 2008-06-23
user1@user1-laptop:/usr/bin$ gnome-panel --display=0
cannot open display: 0
Run 'gnome-panel --help' to see a full list of available command line options.


That happens for all of the numbers I typed in (just a few integers, 0-5 about).

I tried to reinstall the gnome panel:

user1@user1-laptop:/usr/bin$ sudo apt-get install nautilus gnome-panel
[sudo] password for user1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nautilus is already the newest version.
gnome-panel is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But that didn't seem to do anything.

---

### Post by Bubba64 on 2008-06-23
If you right click where the panel should be and then add panel it will install. Then right click on the panel-add to panel to add the main menu for terminal access as well as any thing else you want there.

---

### Post by user1nachi on 2008-06-23
No matter where on the desktop I click it gives me the same options, none of them say anything about panels. I tried all sides of the screen in case the panel had somehow moved, and a substantial portion of the middle through random sampling. No dice anywhere.

---

### Post by kripkenstein on 2008-06-23
> **user1nachi said:**
> user1@user1-laptop:/usr/bin$ gnome-panel --display=0
cannot open display: 0
Run 'gnome-panel --help' to see a full list of available command line options.


That happens for all of the numbers I typed in (just a few integers, 0-5 about).

I tried to reinstall the gnome panel:

user1@user1-laptop:/usr/bin$ sudo apt-get install nautilus gnome-panel
[sudo] password for user1: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nautilus is already the newest version.
gnome-panel is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

But that didn't seem to do anything.
You can try to reinstall gnome-panel, that's an option in synaptic. Also worth trying for gnome-display.

---

### Post by user1nachi on 2008-06-23
How do I install gnome-display?

---

### Post by kripkenstein on 2008-06-23
> **user1nachi said:**
> How do I install gnome-display?

Open synaptic (synaptic from a terminal should work), then search for gnome-display. When you find it, right click on it and select 'reinstall'. Then apply those changes.

---

### Post by user1nachi on 2008-06-23
I don't see gnome-display anywhere after opening synaptic. I tried using the search option, and by looking at all the programs and typing it in. The closest I found was gnome-dbg.

---

### Post by kripkenstein on 2008-06-23
> **user1nachi said:**
> I don't see gnome-display anywhere after opening synaptic. I tried using the search option, and by looking at all the programs and typing it in. The closest I found was gnome-dbg.

Sorry, I thought that existed but I was wrong.

Anyhow, what happens when you reinstall gnome-panel?

---

### Post by user1nachi on 2008-06-23
Nothing. I instead did upgrade, and it put about 38 mbs of stuff in, 17 files. Didn't help. I'm messing around now with other options in usr/bin, near where I found terminal. One, called: gnome-control-center looked promising, but I haven't found anything yet. 

After that, I'll try a few others in there... and if not, just reinstall 8.04. If that doesn't work, i'll take the few files I want to keep, email them to myself, wipe my hard drive, install 8.04 and see if it happens again. If so, back to 7.10 and wait until a new version of 8.04 or the next version comes out. If anyone has any idea's, please let me know, but don't both spending too much time on it unless it piques your interested.

Thank you all for your help.

---

### Post by kripkenstein on 2008-06-23
Yeah, a fresh install might be the easiest solution... It's too bad, but sometimes upgrades fail like that.

---

### Post by dracayr on 2008-06-23
wait a moment...

you can't access a display from one of the tty's.. (except tty7, which is where gnome is loaded to)

but accessing gnome-terminal from nautilus(that's the file browser) should work...

dracayr

---

### Post by misho1721 on 2008-06-23
Edit: whoops there's a page 2

But:
Perhaps this may get something:

sudo apt-get install gnome-panel --reinstall

or even

sudo apt-get remove gnome-panel --purge
sudo apt-get install gnome-panel

since you still have network access if it needs to download anything it will

---

### Post by dracayr on 2008-06-23
look, he hasn't even tried to simply *start* gnome-panel. He tried from a tty, but that was bound to fail...

dracayr

---

### Post by user1nachi on 2008-06-24
How would I do that?

And if you mean go to usr/bin and find gnome-panel and double click on it, that was one of the first things I did. Didn't do anything. It just gives about 5 error messages where the screen flashes each time, and the box disappears before I click on anything, excactly the same thing that happens when it starts up (My assumption would be that starting Ubuntu attempts to launch this, which accounts for the similarities).

---

### Post by meditatingfrog on 2009-08-03
> **user1nachi said:**
> How would I do that?

And if you mean go to usr/bin and find gnome-panel and double click on it, that was one of the first things I did. Didn't do anything. It just gives about 5 error messages where the screen flashes each time, and the box disappears before I click on anything, excactly the same thing that happens when it starts up (My assumption would be that starting Ubuntu attempts to launch this, which accounts for the similarities).

I had an issue with gnome-panel.  Apparently completely removing Evolution (I use gmail) removed gnome-panel as well.  When I reinstalled it using sudo apt-get install gnome-panel, it said Evolution needed to be installed.  

Anyway, gnome-panel is running out of a terminal now, until I reboot.  I was working on another problem when this one came up.  Perhaps you should try typing gnome-panel in a terminal, like I did.  If it doesn't work from the terminal, it isn't going to help to reinstall it.  Perhaps starting Ubuntu in recovery mode might be an option, then try gnome-panel.

---

