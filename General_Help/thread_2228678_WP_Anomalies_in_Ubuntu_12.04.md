---
title: "WP Anomalies in Ubuntu 12.04"
date: 2014-06-08
forum: General Help
---

### Post by kernalkorn on 2014-06-08
Gen comment as much as it is a cry for help.  Libre Ofc Writer became corrupted.  Is there a way to totally purge applications?  Tried uninstalling reinstalling and the same corruption comes up. Libre must recover in order to start.  Then it magically quintupled the font size to humungous (off the page) when viewing/editing rtf files. So it is unusable, won't clear itself out of the system when uninstalled.  Comes back w/ same symptoms.    BTW, removed Libre Write, then used Ubu SoftwareCenter to install Abiword which can read the formats I use.  Abiword seems to start run OK (unlike WriteText which freezes), but looks nothing like the "tourguide" screen shots on the abisource page.  No edit menu.   I kid you not.  Do I have to drop a coin to get the edit menu?   This is extremely strange.   All other functions on the PC seem OK.  Intel C2Duo 2.xmhz w/ nVidia 210 drivers out to HDMi TV, etc etc.  Using PaleMoon Firefox clone browser which also runs perfectly. I can use getedit for some fundamental text work, but I am totally flumuxed and all caddywampus over the fact that somebody makes a WP with no edit menus, function tool bar etc. No context hover menus, no right click context menus, no nuttin'.    I really would like to know how to expurgate an application and all its associated files when corrupted so it can be reinstalled CLEAN and NEW.  I can do it in WinOS using CClean uninstall and registry wipe and delete the residual programs folder, remove application data references and then erase all misc temp files do a TFC reboot etc.  This is about a one year old 12.04 LTS install and has been doing great up until a month ago when the Libre Write started going wrong.

---

### Post by amanchesterman on 2014-06-09
There are purge commands you can use in the terminal to remove a program completely; but I'm never very confident using the terminal, so I tend to use Synaptic instead, marking programs for 'complete removal'. Other, more expert members of this forum can tell you the terminal commands I'm sure.

Either way, the point I want to make here is that removing the *program* is only half the process: you also need to remove the *settings* as well. If your program stops working properly, and you uninstall it and re-install it, and the problem continues as before, then it's probable that the settings are corrupted and maybe not the program itself. 

How to remove the settings? Well, for LibreOffice, you need to open up your file manager and look in your home directory for a folder called '.config'. Chances are you can't see it because folders that begin with a dot '.' are hidden by default. But in your file manager there should be a menu option to 'show hidden folders' (or it may come up if you right-click on the file manager window) and when you do that '.config' should be visible.

Open up the '.config' folder and you should see another folder inside it called 'libreoffice'. Delete that and then restart your machine before trying to re-install LibreOffice, otherwise the new installation inherits all the (corrupted?) settings from before.

The process is similar for AbiWord, but I don't have that installed on my machine so I can't tell you the name and location of the hidden 'abiword' folder. Hopefully someone else on the forum can help with that -- or you can just 'show hidden files' and look for it yourself.

---

### Post by Impavidus on 2014-06-09
+1 to amanchesterman

The terminal command to purge a package is```
sudo apt-get purge <package name>
```but synaptic is also a great tool to do this kind of stuff.

Most likely only the user settings are corrupt, purging and reinstalling the application is probably not even necessary. The user settings of abiword are stored in ~/.config/abiword/.

---

### Post by kernalkorn on 2014-06-09
Problem Solved - Thank You. Cleaned out Libre config fiolder and reinstalled. Used Synaptic to remove Abiword.  Back to abi-normal.   [http://www.youtube.com/watch?v=yH97lImrr0Q](http://www.youtube.com/watch?v=yH97lImrr0Q) Sorry - couldn't resist.

---

### Post by Impavidus on 2014-06-10
Good. Could you mark this thread as solved? Thread tools (near top of page) -> mark as solved.

---

