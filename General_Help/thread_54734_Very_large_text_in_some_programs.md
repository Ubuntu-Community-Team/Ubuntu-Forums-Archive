---
title: "Very large text in some programs?"
date: 2005-08-05
forum: General Help
---

### Post by vvlist on 2005-08-05
I recently installed two programs via synaptic, Skype and PSI 0.9.2. Both of which have text about 18-24pt text... All of my other programs have the system default 10pt. Has anyone had a similar problem?

---

### Post by jonny on 2005-08-05
Dunno about PSI, but Skype uses KDE widgets.  You an control the font size for KDE apps by installing the kcontrol package.  Once installed, you need to run this program from a terminal window using the kcontrol command.

A word of warning, though.  Don't be tempted to run this program as root in the hope of changing the default for all users.  If you try, you'll be unable to use your user name until you've deleted the .ICEauthority file in your home directory.  I know - I have the scars to prove it.

---

### Post by Majlo on 2005-08-06
Hi..

Or install qt3-qtconfig

sudo apt-get install qt3-qtconfig

From the description :
The Qt3 Configuration Application
The Qt Configuration program allows endusers to configure the look
and behavior of any Qt3 application. It is mostly only necessary
on systems which don't run KDE because the KDE control center already
covers this configuration automatically for the users Qt3 applications
according to his desktop settings in KDE. However, if you need to run
CJK-fonts or other non-latin scripts, you will most likely want to
install this package.

Then go to System --> Preferences --> Qt Configuration

And change the font

---

### Post by jonny on 2005-08-06
[QUOTE=Majlo]Hi..

Or install qt3-qtconfig
[/QUOTE]
I've tried using qt3-qtconfig as well as kcontrol.  It's a simpler application so I would have recommended it but, for me, qt3-qtconfig doesn't allow me as wide a choice of widgets as kcontrol does.  I like to use Plastik as it's easy on the eye and similar in spirit to my gnome settings, but I can't select that style unless I use kcontrol.

Both applications work fine with font sizes, though.  But the thing I don't understand is why ubuntu defaults to using such huge fonts in the first place.

---

### Post by kLy on 2005-09-05
[QUOTE=jonny]I've tried using qt3-qtconfig as well as kcontrol.  It's a simpler application so I would have recommended it but, for me, qt3-qtconfig doesn't allow me as wide a choice of widgets as kcontrol does.  I like to use Plastik as it's easy on the eye and similar in spirit to my gnome settings, but I can't select that style unless I use kcontrol.

Both applications work fine with font sizes, though.  But the thing I don't understand is why ubuntu defaults to using such huge fonts in the first place.[/QUOTE]
 Do you have a high res monitor? It's probably to do with your dpi setting rather than font size. On my linux rig, font 12 looks huge but on windoze it looks tiny. Look here:
[http://process-of-elimination.net/index.php?title=Control_Font_DPI_in_X](http://process-of-elimination.net/index.php?title=Control_Font_DPI_in_X)

---

### Post by skoal on 2005-09-05
One thing I noticed in KDE is that you need to set your root (sudo) fonts as well as your normal user ones.  Otherwise, when you fire up certain apps requiring root privileges, you get those big (default) fonts (for those specific apps).  Well, you can't login as root in KDE...

My sol'n: right click over KControl > Menu Editor > Control Center > X - Run as different user.  Then, fire up control center, login as root, and set fonts for root.  After that, go back and remove the "X" for run as different user for Control Center app, so you will have normal non-root user access to it.

Kynaptic and other root privy apps then had the fonts I wanted.  GTK apps like Synaptic which also require root privs do not have that same issue while running in a KDE shell...

\\//_

---

### Post by kLy on 2005-09-05
If you change the DPI, the font sizes will change globally. Then you can use 12pt fonts as they really are meant to be... normal size. Not huge

---

