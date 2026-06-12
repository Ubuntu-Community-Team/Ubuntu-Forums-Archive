---
title: "Auto login to command line and execute Python script"
date: 2018-08-29
forum: General Help
---

### Post by jbonde on 2018-08-29
Is it possible in Ubuntu 18.04 to configure the boot process disabling the GUI and instead booting directly to the command prompt and then run a python script without the need of keyboard and mouse? Used to work fine with rc.local but this feature has now been discontinued as far as I can see.
br Jesper

---

### Post by TheFu on 2018-08-29
You can re-enable rc.local. It is just controlled by systemd now.

---

### Post by jbonde on 2018-09-02
Can't make that work. Any other suggestions?

---

### Post by webmiester on 2018-09-02
How about this idea?  Sorry Im not an expert so Im not sure if this will work yet.  Just an idea.

1) Uninstall the gui so that the system is forced to bootup into a command line automatically

2) Write your python script and save it at /.config/autostart

Dont forget to make your python script execuatble.

Im looking forward to comments on this idea.

---

### Post by TheFu on 2018-09-02
> 
2) Write your python script and save it at /.config/autostart

This is a GUI-only thing, might be limited to gnome-only. IDK.  It won't work without some GUI forcing it. Good idea, but ... nope.

I don't have 18.04. My latest systems run 16.04 and rc.local works.  18.04 changed many things.

---

### Post by webmiester on 2018-09-03
> **TheFu said:**
> This is a GUI-only thing, might be limited to gnome-only. IDK.  It won't work without some GUI forcing it. Good idea, but ... nope.

I don't have 18.04. My latest systems run 16.04 and rc.local works.  18.04 changed many things.

Thank you for correcting me.

I remember DOS would have autoexe.bat which was the first file the OS looks for and loads upon bootup.  Does ubuntu have some sort of equivalent to this?

---

### Post by Holger_Gehrke on 2018-09-04
To disable the GUI with systemd you have to set the default target:```
systemctl set-default multi-user.target
```To return to booting into the GUI you'd set graphical.target as default. /etc/rc.local will be pulled in through systemd-rc-local-generator, but the file has to be executable and must start with a shebang or hashpling or whatever else you want to call a line saying something like ```
#!/bin/bash'
```
Holger

---

### Post by jbonde on 2018-09-08
Yes, but using the multi-user.target will require login as I need to type username and passsword for each boot. Need to find a solution that will boot and execute a python script without use of keyboard as my application is made for a touch screen.

---

### Post by dragonfly41 on 2018-09-08
I would experiment with an automation script which *emulates* key presses on your touch screen.
Thus the script launched after booting would run through emulation of login, creating username and password, much like a macro.
If that is an option I can point to several approaches I use.

---

### Post by jbonde on 2018-09-08
Thanks - sounds like it's worth trying. So please give some directions if there is no possibility of automatic login to command prompt

---

### Post by jbonde on 2018-09-08
Just a quick update. Did install Ubuntu 16.04 LTS which I noticed was previously recommended for the Intel NUC that I have. Here the rc.local is available and by updating this with the path to my python script everything works like a charm just like the Raspberry Pi that I used previously.  
So thanks a lot for your support! Hope that future editions of Ubuntu will feature similar possibilities as it has taken too much time to realize that command line autologin and python execution is not possible in version 18.04.

---

