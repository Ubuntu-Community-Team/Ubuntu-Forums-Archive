---
title: "Ubuntu 13.04 64 no launcher or top panel"
date: 2013-10-12
forum: General Help
---

### Post by hunterkasy on 2013-10-12
I have a hp pavalilion g7 laptop running a quad core amd with 8 gigs of memory and a ssd hhd that has Ubuntu 13.04 64 with the latest updates installed.

the problem I am having is I just turned on my lappy and logged in just fine but only the desktop shows up no launcher or top panel.  I need help on this thanks

---

### Post by stinkeye on 2013-10-13
If you can open a terminal with ctrl+alt+t...
Run...
```
sudo apt-get install compizconfig-settings-manager
```

then run ...
```
ccsm
```

and check the **ubuntu unity plugin** is enabled.
Unlike the other plugins you have to click on it to see the enable box to the left.

---

### Post by hunterkasy on 2013-10-13
I did that and still nothing, when I go back into ccsm the check for the UUP is unchecked and I try to enable it but nothing

---

### Post by stinkeye on 2013-10-13
> **hunterkasy said:**
> I did that and still nothing, when I go back into ccsm the check for the UUP is unchecked and I try to enable it but nothing
Is it a fresh install or upgrade?
Was unity running before?
Have you installed anything or done some tweaks that may have caused it.

Your terminal output from
```
/usr/lib/nux/unity_support_test -p
```

eg
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **/usr/lib/nux/unity_support_test -p**
OpenGL vendor string:   NVIDIA Corporation
OpenGL renderer string: GeForce GTX 550 Ti/PCIe/SSE2
OpenGL version string:  4.3.0 NVIDIA 310.44

Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

---

### Post by hunterkasy on 2013-10-13
I also get a pop up that says:

no system tray detected on this system
unable to start, exiting

---

### Post by hunterkasy on 2013-10-13
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ /usr/lib/nux/unity_support_test -p
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$

---

### Post by hunterkasy on 2013-10-13
I have been running off of a fresh install of 13.04 unity was working just fine everything was working fine, did no tweaks or installed anything

---

### Post by stinkeye on 2013-10-13
> **hunterkasy said:**
> I have been running off of a fresh install of 13.04 unity was working just fine everything was working fine, did no tweaks or installed anything

You may want to install the gnome fallback session while your trying to get it to work.
```
sudo apt-get install gnome-panel
```
This will give you 2 extra login sessions.
Both use the gnome-panel.
[LIST]
[*]gnome fallback......uses compiz
[*]gnomefallback(no effects).....uses metacity
[/LIST]

Try the **gnome fallback** session to see if it will load with compiz.
If not, try the **gnomefallback(no effects)** session.

You can also try in the **ubuntu** session to reset and reload unity...
```
dconf reset -f /org/compiz/ && setsid unity
```

---

### Post by hunterkasy on 2013-10-13
I tried reset and reload unity and this is what I got:

tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ dconf reset -f /org/compiz/ && setsid unity
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ compiz (core) - Info: Loading plugin: core
compiz (core) - Info: Starting plugin: core
unity-panel-service: no process found
compiz (core) - Info: Loading plugin: ccp
compiz (core) - Info: Starting plugin: ccp
compizconfig - Info: Backend     : gsettings
compizconfig - Info: Integration : true
compizconfig - Info: Profile     : unity
compiz (core) - Info: Loading plugin: composite
compiz (core) - Info: Starting plugin: composite
compiz (core) - Info: Loading plugin: opengl
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Info: Unity is not supported by your hardware. Enabling software rendering instead (slow).
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Info: Unity is undetectable
/usr/lib/nux/unity_support_test: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
compiz (core) - Info: Unity is undetectable
compiz (core) - Error: Failed to load plugin: opengl
compiz (core) - Info: Loading plugin: copytex
compiz (core) - Error: Failed to load plugin: copytex
compiz (core) - Info: Loading plugin: decor
compiz (core) - Error: Failed to load plugin: decor
compiz (core) - Info: Loading plugin: grid
compiz (core) - Error: Failed to load plugin: grid
compiz (core) - Info: Loading plugin: move
compiz (core) - Error: Failed to load plugin: move
compiz (core) - Info: Loading plugin: regex
compiz (core) - Info: Starting plugin: regex
compiz (core) - Info: Loading plugin: place
compiz (core) - Info: Starting plugin: place
compiz (core) - Info: Loading plugin: compiztoolbox
compiz (core) - Error: Failed to load plugin: compiztoolbox
compiz (core) - Info: Loading plugin: session
compiz (core) - Info: Starting plugin: session
compiz (core) - Info: Loading plugin: mousepoll
compiz (core) - Info: Starting plugin: mousepoll
compiz (core) - Info: Loading plugin: gnomecompat
compiz (core) - Info: Starting plugin: gnomecompat
compiz (core) - Info: Loading plugin: snap
compiz (core) - Info: Starting plugin: snap
compiz (core) - Info: Loading plugin: vpswitch
compiz (core) - Info: Starting plugin: vpswitch
compiz (core) - Info: Loading plugin: resize
compiz (core) - Error: Failed to load plugin: resize
compiz (core) - Info: Loading plugin: wall
compiz (core) - Error: Failed to load plugin: wall
compiz (core) - Info: Loading plugin: imgpng
compiz (core) - Info: Starting plugin: imgpng
compiz (core) - Info: Loading plugin: animation
compiz (core) - Error: Failed to load plugin: animation
compiz (core) - Info: Loading plugin: unitymtgrabhandles
compiz (core) - Error: Failed to load plugin: unitymtgrabhandles
compiz (core) - Info: Loading plugin: expo
compiz (core) - Error: Failed to load plugin: expo
compiz (core) - Info: Loading plugin: fade
compiz (core) - Error: Failed to load plugin: fade
compiz (core) - Info: Loading plugin: scale
compiz (core) - Error: Failed to load plugin: scale
compiz (core) - Info: Loading plugin: workarounds
compiz (core) - Error: Failed to load plugin: workarounds
compiz (core) - Info: Loading plugin: ezoom
compiz (core) - Error: Failed to load plugin: ezoom
compiz (core) - Info: Loading plugin: unityshell
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$

---

### Post by hunterkasy on 2013-10-13
I logged in by this:
gnome fallback......uses compiz

the 2 panels show up but I am unable to play any videos in vlc I get this:

no system tray detected on this system
unable to start, exiting

---

### Post by stinkeye on 2013-10-13
> **hunterkasy said:**
> I logged in by this:
gnome fallback......uses compiz

the 2 panels show up but I am unable to play any videos in vlc I get this:

no system tray detected on this system
unable to start, exiting

Install this small application
```
sudo apt-get install wmctrl
```

Then while in the gnome fallback session
Run...
```
echo $DESKTOP_SESSION && wmctrl -m | head -n1
```
That will confirm the session and window manager running.
Just want to check compiz is running.

The **libGL.so.1** error appears to be a gfx driver issue and not really sure how to fix.
Could try reinstalling your driver.

The output from this command would also be helpful to show gfx card and driver in use.....
```
lspci -nnk | grep -iA2 vg
```


You could also try the reinstallation of this package.
```
sudo apt-get install --reinstall libgl1-mesa-glx
```

---

### Post by hunterkasy on 2013-10-13
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ echo $DESKTOP_SESSION && wmctrl -m | head -n1
gnome-fallback-compiz
Name: Metacity
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$

tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ lspci -nnk | grep -iA2 vg
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI BeaverCreek [Radeon HD 6520G] [1002:9647]
	Subsystem: Hewlett-Packard Company Device [103c:3568]
	Kernel driver in use: fglrx_pci
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$ 

tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$     sudo apt-get install --reinstall libgl1-mesa-glx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 0 not upgraded.
Need to get 208 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
tyler@tyler-HP-Pavilion-g7-Notebook-PC:~$

---

### Post by stinkeye on 2013-10-13
From your output compiz isn't even starting and your dropping back to
metacity as your window manager.


I'm wondering why you got the abort message when
running ...
```
sudo apt-get install --reinstall libgl1-mesa-glx
```

It should continue if you enter "y" or "Y" or just leave blank and press Enter.
```
[COLOR="#008000"]glen@Raring:~$[/COLOR] **sudo apt-get install --reinstall libgl1-mesa-glx**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  cli-common libdbusmenu-qt5 libelf1:i386 libgdiplus linux-image-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 2 not upgraded.
Need to get 0 B/208 kB of archives.
After this operation, 0 B of additional disk space will be used.
**Do you want to continue [Y/n]?** 
(Reading database ... 400961 files and directories currently installed.)
Preparing to replace libgl1-mesa-glx:amd64 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-glx_9.1.4-0ubuntu0.1_amd64.deb) ...
Unpacking replacement libgl1-mesa-glx:amd64 ...
Preparing to replace libgl1-mesa-glx:i386 9.1.4-0ubuntu0.1 (using .../libgl1-mesa-glx_9.1.4-0ubuntu0.1_i386.deb) ...
Unpacking replacement libgl1-mesa-glx:i386 ...
Setting up libgl1-mesa-glx:amd64 (9.1.4-0ubuntu0.1) ...
Setting up libgl1-mesa-glx:i386 (9.1.4-0ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

Try again and just hit the Enter key at the **[Y/n]?** prompt.

ps To put long code in code blocks you need to be using "Adv Reply"  and after pasting in 
your code, highlight with the left mouse button and then hit the # icon at the top to enclose in code blocks.
[ATTACH=CONFIG]246932[/ATTACH]

---

### Post by hunterkasy on 2013-10-13
> sudo apt-get install --reinstall libgl1-mesa-glx

was able to get to install, but it did nothing to getting it back working

---

### Post by stinkeye on 2013-10-13
> **hunterkasy said:**
> was able to get to install, but it did nothing to getting it back working

Ok.
I asked someone else to have a look at this thread as I have little
experience with amd gfx.
GoodLuck.

---

### Post by tgalati4 on 2013-10-13
Well you have tried a lot of things and still not working.  What is the SMART status of this disk drive?

```
sudo smartctl -a /dev/sda
```

libGL.so.1 is missing or broken and that will ball things up.  We need to figure out why it is missing.

What is the output of:

```
fglrxinfo
```

You might want to go through this tutorial in detail:  [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

Also go through the following log files:

```
cat /var/log/Xorg.0.log
cat ~/.xession-errors
```

Paste any helpful messages.

---

