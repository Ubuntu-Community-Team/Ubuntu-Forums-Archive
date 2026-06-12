---
title: "[SOLVED] Compiz Fusion problem"
date: 2007-09-08
forum: General Help
---

### Post by s_h_a_d_o_w_s on 2007-09-08
I installed compiz-fusion with

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

But the window decorator is the normal ubuntu one, and if i make a setting change in the compiz settings, they dont apply, cause there's no wobbly or cube

Thanks :)

---

### Post by smithman89 on 2007-09-08
did you try: 
Alt + F2```
compiz --replace
```
Compiz wont run without that command either invoked by the user or in the startup command list.
The compiz config settings manager only applies options to compiz (not metacity, the default window manager).  Also, choose the window manager setting in ccsm so that your window borders will show.

---

### Post by s_h_a_d_o_w_s on 2007-09-08
Thanks for the reply! :D

Here's le output:
```

giga@UbuntuZilla:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking for nVidia: present. 
Checking for Xgl: not present. 

(gtk-window-decorator:5756): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5756): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5756): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5756): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5756): Wnck-WARNING **: Unhandled action type (nil)

(gtk-window-decorator:5756): Wnck-WARNING **: Unhandled action type (nil)



```

I feel rly noobish :S

I need xgl what do i do?

And for the command to put into ccsm, 

do i put 

emerald or emerald --replace as the command, and, dfo i put it in Command, Decoration Windows or Shadow Window? (in the Window Decoration button)

---

### Post by g2g591 on 2007-09-08
try sudo apt-get install xserver-xgl . Im not sure if the package name is the same (but it proabilbly is) as the gutsy repos.

---

### Post by s_h_a_d_o_w_s on 2007-09-08
giga@UbuntuZilla:~$ sudo apt-get install xserver-xgl
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
xserver-xgl is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
giga@UbuntuZilla:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"






Thanks for replying though ::DD

---

### Post by g2g591 on 2007-09-09
Hmm, try running sudo nvidia-xconfig --add-argb-glx-visuals -d 24

---

### Post by s_h_a_d_o_w_s on 2007-09-09
sudo nvidia-xconfig --add-argb-glx-visuals -d 24giga@UbuntuZilla:~$ sudo nvidia-xconfig --add-argb-glx-visuals -d 24
Password:

Using X configuration file: "/etc/X11/xorg.conf".
Option "AddARGBGLXVisuals" "True" added to Screen "Default Screen".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

giga@UbuntuZilla:~$ compiz --replace
Checking for Xgl: not present. 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

giga@UbuntuZilla:~$ 







Thanks though :D Any other ideas? :)

---

### Post by s_h_a_d_o_w_s on 2007-09-10
Bump :D

---

### Post by Bruegger on 2007-09-12
Hey dude, did you solve this problem?
could you share your workaround with us?

---

### Post by s_h_a_d_o_w_s on 2007-09-12
Yeah sure sorry :P

It's cause i had some beryl stuff/extra repos installed that i neeeded to remove.

So basically you follow this guide:

[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

And make sure you only have their repos

Once the Compiz Fusion packages were isntalled they wouldnt run, but a restart fixed that. It was written on the guide.

And i didnt know the  difference between the ubuntu default window decorator and emerald, so I added

```
compiz ---replace
```

and 

```
emerald --replace
```

to startup

---

