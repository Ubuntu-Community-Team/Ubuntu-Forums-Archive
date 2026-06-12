---
title: "I made a small (big) mistake when trying to customize Ubuntu.."
date: 2014-11-22
forum: General Help
---

### Post by kohl2 on 2014-11-22
Soo I have been having troubles up the wazoo so far with this run of playing with Ubuntu.
(I think I may go back to an older version, I previously played around with 12.something and I remember enjoying it much more)

Either way, after setting up Ubuntu 14.04 on my laptop I began to customize it. During this customization I downloaded a couple applications to help me (Unity tweak and Gnome tweak). 
When playing around with the "Gnome Tweak" tool, I clicked on the setting under 'effects' That had something to do with being able to customize the border of windows.
And so a pop up came up, it said something about how this will disable some other kind of Unity effect, I did it anyway.
Whoops.
After turning the option back off because I liked the other style (that I disabled) better, now there are no borders to any windows, no windows equivalent start menu bar thing, and no task tray.

Unfortunately I didn't even set a hotkey for the terminal.

Please help me!

---

### Post by coldraven on 2014-11-22
Is this any use?
[http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/](http://ubuntuhandbook.org/index.php/2014/04/reset-unity-and-compiz-settings-in-ubuntu-14-04/)

---

### Post by flaymond on 2014-11-22
Terminal default hotkeys is CTRL+ALT+T 


Your mistake is our mistake, so we will solve it ..together.

---

### Post by buzzingrobot on 2014-11-22
If you are using Gnome Tweak Tool (although it does not include an "Effect" section) be careful.  It's intended for Gnome, not Unity. There are components of Gnome used in Unity, but the toolsets that draw and manage windows, window controls, are not the same.

---

### Post by CantankRus on 2014-11-22
What I believe you used was compizconfig-settings-manager to enable the window decorations plugin under "effects".
In 14.04 the Ubuntu Unity plugin handles window decorations.
If you enable the window decorations plugin the Ubuntu Unity plugin is disabled.....ie no panel or launcher.

You should still be able to open a terminal with ctrl+alt+t and run compizconfig-settings-manager with...
```
ccsm
```

Disable the window decorations plugin and enable the Ubuntu Unity plugin.

If fails to return to normal reset unity as in **coldraven's** link, with...
```
dconf reset -f /org/compiz/
```

Then logout with...
```
kill -9 -1
```

---

### Post by kohl2 on 2014-11-22
Ctrl+Alt+T doesnt do anything. :(

Is there any kind of 'safe mode' I might be able to boot up in, something that would load default setting from which I could change stuff back to normal?

I'm much more used to Windows machines, so forgive my lack of terminology if I'm butchering this..

Thank you guys so much for any help! This is really a great forum site!

---

### Post by kohl2 on 2014-11-22
On a different, more technical note, I have configured my laptop to be able to dual-boot windows 8 as well as Ubuntu, however this computer has the weirdest BIOS menu/settings ever.

So in order to boot my computer up in windows, I have to make sure my 'boot mode' in the 'advanced settings' tab must be set to 'UEFI' mode or something, where to boot in Ubuntu it must be set to 'CSM'. 

I may need to just post a new thread about this, but is there any way to be able to not have to pull up my BIOS menu whenever I want to switch the OS my comp starts up on?

---

### Post by mc4man on 2014-11-22
> **kohl2 said:**
> Ctrl+Alt+T doesnt do anything. :(

Is there any kind of 'safe mode' I might be able to boot up in, something that would load default setting from which I could change stuff back to normal?

I'm much more used to Windows machines, so forgive my lack of terminology if I'm butchering this..

Thank you guys so much for any help! This is really a great forum site!
If you have a folder on the Desktop just open it & navigate from Computer  to /usr/share/applications, find the CompizConfig Settings Manager icon & d. left click on, ect.
If you don't have a folder on the Desktop then r. click on the Desktop > New Folder & use that one

If you can get to /usr/share/applications but using CompizConfig Settings Manager proves not possible then d. click on the Terminal icon & run command in post 5

---

### Post by sotiris2 on 2014-11-24
If that also doesn't work you can drop on a console with Ctrl+Alt+F1, login again and try ```
[COLOR=#000000][FONT=Ubuntu Mono]dconf reset -f /org/compiz/
``` then get back at graphics with Ctrl+Alt+F7 and logout relogin. If you can't because the interface is not working you can drop back to the console and restart the system with ```
sudo restart now
```
[/FONT][/COLOR]

---

### Post by CantankRus on 2014-11-24
To run dconf reset when logged into a tty you need to specify an X11 $DISPLAY.
eg
```
DISPLAY=":0" dconf reset -f /org/compiz/
```

---

