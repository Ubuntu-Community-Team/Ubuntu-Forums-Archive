---
title: "Using &quot;compiz --replace&quot; in a script"
date: 2008-06-22
forum: General Help
---

### Post by burnttoast11 on 2008-06-22
I am trying to make a perl script that can change the window manager to compiz or metacity.  The problem I am having is that after the script is done running, if I close the terminal the window borders will disappear.  I know that I can use the Alt-F2 -> "compiz --replace" and I won't need to have an open terminal, but I was wondering how I could do this from within a script.
Thanks!

---

### Post by pietjanjaap on 2008-06-22
That is because you have something not installed correct.

1 do this then compiz does not start with ubuntu, and you don't get the white screen.

Stop Compiz-Fusion From Loading Automatically

This guide will show you how to stop Compiz-Fusion from loading automatically on startup in Hardy Heron and how to setup a shortcut for launching Compiz when you want.

Step 1: Run gconf-edit
Start Run Application by pressing Alt+F2

Screenshot-Run Application

Enter gconf-editor into the box, hit enter


Step 2: Set Metacity as your default start up window manager
Once in gconf-editor navigate to desktop>gnome>applications>window_manager

Screenshot-Configuration Editor - window_manager

under current and default replace each instance of:
/usr/bin/compiz with /usr/bin/metacity
it should like this when you're done:

Screenshot-Configuration Editor - window_manager-1



Step 3: Create a shortcut for starting Compiz-Fusion
right click the Applications Places System Menu
select the Edit Menu option

Screenshot-Main Menu

pick a location for your shortcut and select New Item box

Screenshot-Launcher Properties
Type: Application
Name: Compiz
Command: compiz --replace
COmment compiz window manager


2 try this:
dpkg-reconfigure xserver-xorg is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the x,
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

3



4

Setup Compiz Fusion with open source ati radeon drivers

Older ATI cards have been blacklisted for Compiz Fusion because of a bug in the driver, but there is an easy workaround for many cards that use the open source ati drivers. Radeon 9500 are the oldest cards to support the restricted "fglrx" drivers, so everything older requires the open source drivers to function properly.



First edit the launcher for Compiz Fusion:

gksudo gedit /usr/bin/compiz

Near the top, add the line

SKIP_CHECKS="yes"

I added it under VERBOSE="yes"

You may also need to install the Compiz settings manager program that you can access from System->Preferences->Advanced Desktop Effect Settings | 1-click install or:

sudo apt-get install compizconfig-settings-manager

You can now load Compiz Fusion with

compiz --replace

and revert to Metacity (the basic window manager) with

metacity --replace

I suggest making launchers in a panel for this.

Remember that this is a workaround and may not work for everybody. If you have further problems, you should consider running a forum search and then posting on one of the main support forums if you still need help.
For the record, my card is an ATI Mobility Radeon 9000.

---

### Post by burnttoast11 on 2008-06-22
Thanks for the reply, but I don't think you understand the question.  I have no problem using compiz or metacity.  They both work fine.  I know how to use the 'compiz --replace' and metacity --replace' command by typing them in a 'Run Application' box (Alt-F2).  Basically, I was wondering how I could do the equivalent of pressing Alt-F2 and entering a command from a perl script.
Thanks.

---

### Post by ad_267 on 2008-06-22
Try using "nohup compiz --replace &" instead.

Edit: You can also use "(exec compiz --replace &)"

---

### Post by burnttoast11 on 2008-06-22
hmmm, I get the following message if I type that in the terminal,
nohup: ignoring input and appending output to `nohup.out'

---

### Post by ad_267 on 2008-06-22
> **burnttoast11 said:**
> hmmm, I get the following message if I type that in the terminal,
nohup: ignoring input and appending output to `nohup.out'

Sorry I edited my post. Did you put the & on the end? It should work.
You can also use "(exec compiz --replace &)"

---

### Post by ad_267 on 2008-06-22
Oh and if you're using nohup you might want to use this so it doesn't create a nohup.out file:

```
nohup compiz --replace > /dev/null &
```

---

