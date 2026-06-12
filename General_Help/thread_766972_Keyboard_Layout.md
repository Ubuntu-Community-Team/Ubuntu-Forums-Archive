---
title: "Keyboard Layout"
date: 2008-04-25
forum: General Help
---

### Post by HuckleSmothered on 2008-04-25
Just recently upgraded from Gutsy to Hardy.

Since then, I have been unable to set a new keyboard layout. Specifically, I'm trying to use the Dvorak layout. Setting it up in the **System | Preferences | Keyboard** window changes it ... until the next reboot.

Even when I remove all other options besides Dvorak and restart, Qwerty wins. I can't even change it by using the keyboard shortcut set up to switch.

Checked the /etc/X11/xorg.conf file. 
Looks like this for the relevant section:

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Luckily, I back up my junk before big updates. On the previous working Gutsy, the xorg.conf file looks EXACTLY the same for this section. So I suspect that the keyboard layouts have nothing to do with xorg.conf. But where IS the disconnect then?

---

### Post by nico_h on 2008-04-29
same problem !

---

### Post by Vion on 2008-04-29
same problem here!!!

---

### Post by Zorael on 2008-04-29
You should be able to pick the layout you want if you reconfigure xorg.
```
$ sudo dpkg-reconfigure xserver-xorg
```
Do note that you'll (most likely) lose videocard settings upon doing this, so make a proper backup of your /etc/X11/xorg.conf.

X seems to have undergone some changes as to what is needed in xorg.conf, so perhaps this is one of those issues. My advice for upgraders is to completely redo the file (backing it up, reconfiguring, comparing the files and restoring video options).

---

### Post by nico_h on 2008-04-29
well, i tried this solution and i noticed two things :

- i didn't know exactly which option to choose to get my preferred keyboard again

- it looked like editing the keyboard section of xorg.conf

i also had another hint from another ubuntu forum, that was to check the file /etc/X11/xkb/symbols/fr

(i got a french keyboard)

and well i finally noticed that this file contained keyboard layout descriptions and that they all have a name, like :
```
 xkb_symbols "latin9" { ......
```
or ```
 xkb_symbols "oss" { ..... 
```
etc.

with the layout matching "oss" being the same that was currently running and that i didn't want.

this name was precisely the one reported in xorg.conf there :

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"oss"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

so i just edited xorg.conf and changed oss to latin9 (the one i wanted) so this chunk of xorg.conf looks like :

```
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"fr"
	Option		"XkbVariant"	"latin9"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection
```

AND it works !


I just wonder why gnome (control center) didn't do that itself.

isn't it a bug ?

---

### Post by nico_h on 2008-04-30
no it was no bug.  it showed up because i ran gnome-control-center from e17 instead of from gnome.

but though, if i just do the change in gnome then the login screen is still in the wrong config (the gnome gui lets change the user config, not the whole) so editing xorg.conf (as well as answering right to the questions of sudo dpkg-reconfigure xserver-xorg) resolves the problem for the login screen also.

---

### Post by Vion on 2008-05-01
My situation is somewhat more intricate. A heve several accounts on my computer. And the issue occurs only in one of the account while it works smoothlessly on the other ones.

---

### Post by nico_h on 2008-05-01
does the xorg.conf editing not fix the problem for *all* users ? (actually if you want a different keyboard layout for each user, it's not the good solution)

---

### Post by Metallinut on 2008-05-02
Is there any other fixes for this?  I'd like to still be able to switch between US Default and US Dvorak.  I had no problem doing this with Gutsy, but ever since the upgrade to Hardy its all QWERTY all the time :(

I went so far as to remove default from the list of keyboard layouts in Keyboard Preferences, so that Dvorak is the ONLY one listed.  Keyboard still responds with QWERTY.  I can even right-click on the keyboard indicator, choose "Show Current Layout" and it shows a Dvorak keyboard layout...yet all typing comes out QWERTY!

FTW!!!11eleven

---

### Post by manofskill on 2008-06-10
I'm just having the same problem in Ubuntu 8.04(Hardy) 64bit and I'm having to type this in Qwerty which is not my normal mode.  I think you have to include the line:
[INDENT]
[COLOR="Red"]Option	"XkbVariant""dvorak"[/COLOR][/INDENT]

in the Section "InputDevice" that coresponds to your keyboard in your /etc/X11/xorg.conf file.


I have a "Microsoft Keyboard Elite for Bluetooth" with all the extra keys working.  Mine looks like:

[INDENT]Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
	[COLOR="Red"]Option		"XkbVariant"	"dvorak"[/COLOR]
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection[/INDENT]

---

