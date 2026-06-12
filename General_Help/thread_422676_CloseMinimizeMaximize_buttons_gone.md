---
title: "Close/Minimize/Maximize buttons gone"
date: 2007-04-25
forum: General Help
---

### Post by thekingraptor on 2007-04-25
Im running ubuntu edgy and yesterday sometime my Close/Minimize/Maximize buttons dissapeared, in fact the entire bar was gone. Im not sure what you call that bar which is probably why i cant find any other posts about this sort of problem. I was just wondering if anyone else had this happen.

As far as I know I didnt change any settings, I know i didnt uninstall anything.

thanks for your help!!

---

### Post by hyperair on 2007-04-25
It's called window titlebar, and I think you're missing the window borders as well. The entire thing is called window decorations, and which window manager are you using? Beryl/Compiz? or Metacity? or some other?

---

### Post by richardi on 2007-04-26
I have the same problem - the windows also seem glued to the top left corner of the workspace and cover the gnome taskbar at the top of the screen. This happened on Feisty using a previous kernel immediately following an update of 4 packages which were something to do with Gnome (can't remember what they were). Any help appreciated.
Thanks
Richard

---

### Post by anaconda on 2007-04-26
you can get them back by typing these command in terminal:

for normal ubuntu window-manager:
```
metacity
```

or if you haveinstalled  beryl

```
beryl-manager
```

the metacity is more robust and reliable even if you have beryl installed, but beryl special effects wont work with metacity..

and I think that if you run metacity it will disable beryl and next time you boot you will have metacity..

---

### Post by hyperair on 2007-04-26
The windows sticking to the top left of the screen occurs when you have no window manager running. In that case, you can either do what anaconda said, or just tinker around with the window managers list in the Beryl tray icon.

---

### Post by tomole on 2007-04-26
I had the same problem after I allowed the update manager to upgrade from edgy to feisty.
 I stumbled on the solution for the windows problem . I went to "system-preferences-desktop effects" and clicked "enable". However I didn't allow the effect to remain in effect and canceled it. When I next  reopened a window, everything was back to normal....

---

### Post by hyperair on 2007-04-26
Well if you disable desktop effects then you'll be using Metacity as your window manager, and Metacity is its own window decorator so you will not have any problems with the window borders.

---

### Post by richardi on 2007-04-26
tomole - I tried that but the tick boxes in the desktop effects dialogue box are greyed out and I can click enable but nothing changes. Will do metacity in terminal now.
cheers
Richard

---

### Post by jannevanhecke on 2007-09-19
i have the same problem in 7.10
Can anybody help?

---

### Post by jannevanhecke on 2007-09-19
nobody?

---

### Post by reneaguirre on 2007-10-30
Using Ubunto 7.10, I just had the same issue, solution...

Right click on your desktop, try to change your wallpaper, then switch to the visual effects tab, finally just select the option to not use any effect at all... that's it.

You'll recover the title bar.

---

### Post by hyperair on 2007-10-30
By clicking on no effects, you'll revert back to using Metacity. Drawback is you don't have any effects enabled in your system after that.

---

### Post by tynen on 2007-10-30
I tried the meta city thing but this si what happened


syn@Copper:~$ metacity
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
syn@Copper:~$ beryl-manager
bash: beryl-manager: command not found
syn@Copper:~$ metacity
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
syn@Copper:~$ metacity --replace

now all of my windows are acting funky.

---

### Post by hyperair on 2007-10-30
If you're using Gutsy, use the Appearance applet to set it to no effects. If you're using Feisty, make sure your Desktop Effects is set to off. Otherwise, use this command:
```
metacity --replace
```

---

### Post by linux4me on 2007-10-30
I have the same problem periodically in 7.10 (Gutsy). 

I don't want to give up my effects, so I fix it by going System -> Preferences -> Appearance -> Visual Effects -> None. This gets the titlebar, borders, etc. back. Then I click "Extra" to get my visual effects back and the titlebars stick around. 

The titlebars disappearing only seems to happen about once in every 5-6 reboots. (I turn the machine off at night.)

---

### Post by hyperair on 2007-10-30
Oh in that case it's just some random crashing of gtk-window-decorator or emerald. If you're using emerald just open your run dialog and type emerald. Otherwise just type gtk-window-decorator. Your titlebars should come back after that. Or just type compiz in the run dialog. That'll automatically select whether to use emerald or not.

---

### Post by Sportsdude11751 on 2008-01-21
well i was having this problem typed the last post gtk-window-decorator and it worked, but when I closed terminal it stopped.

---

### Post by hyperair on 2008-01-22
Use the run dialog, not the terminal. Or in the terminal.. type
```

gtk-window-decorator &

```
and close the terminal by pressing Ctrl+D or typing "exit". The "&" runs the task in background, and "exit"/Ctrl+D closes the shell gracefully so that background tasks can continue running.

---

### Post by icy on 2008-03-10
hi all..I'm trying to figure out if theres a permanent fix for the window decorations disappearing in gutsy..
metacity --replace and setting Appearance->Visual Effects to none work temporarily till the next reboot. gtk-window decorator has no effect.
Everything worked fine when i first installed gutsy a week back. I also cant seem to get the sound working on this machine.
heres my compiz output:
:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator

Any tips/tricks would be appreciated.

---

### Post by hyperair on 2008-03-10
If you're using an nVidia card, then run this command: ```
sudo nvidia-xconfig --add-argb-glx-visuals
```

Then restart X (Ctrl+Alt+Backspace) or restart your computer.

As for sound issues, go google for snd-hda-intel and Gutsy. That should give you many different articles with many different fixes for different platforms. I think the simplest of them all is to install linux-backports-modules for your kernel.

---

### Post by icy on 2008-03-10
thanks for the prompt reply and getting me on the right track hyperair!
so..this is what i did:
:~$ sudo apt-get install nvidia-glx
:~$ sudo nvidia-xconfig --add-argb-glx-visuals

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'
That solved the window decoration disappearing issue and I'm also enjoying high screen resolution now :) 
Thanks for the sound tip too.

---

### Post by hyperair on 2008-03-10
No problem.

---

