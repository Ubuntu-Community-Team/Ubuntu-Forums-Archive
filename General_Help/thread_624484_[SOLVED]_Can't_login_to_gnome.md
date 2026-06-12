---
title: "[SOLVED] Can't login to gnome"
date: 2007-11-27
forum: General Help
---

### Post by aliencam on 2007-11-27
Hello, I started getting this error a long time ago, and have been forced to use gnome-failsafe ever since the error began. 

I don't remember what I was doing because it was weeks ago. it just so happens that the day after my problem starts, my PSU starts spouting smoke... it's taken a long time to get the PSU replaced.  

but now i have it done, and need to get this problem solved.. 


When I log into Gnome, I get the "your session has lastes less than 10 seconds" error, which I have had before when i messed stuff up... 

The Failsafe gnome session works perfectly. 

Here is my .xsession-errors file. 


```
(process:5514): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5518): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
/home/cameron/.profile: 1: [scaleaddon]: not found
/home/cameron/.profile: 2: as_close: not found
/home/cameron/.profile: 3: as_zoom: not found
/home/cameron/.profile: 4: s0_window_title: not found
/home/cameron/.profile: 5: s0_title_bold: not found
/home/cameron/.profile: 6: s0_title_size: not found
/home/cameron/.profile: 7: s0_border_size: not found
/home/cameron/.profile: 8: s0_font_color: not found
/home/cameron/.profile: 9: s0_back_color: not found
/home/cameron/.profile: 10: s0_window_highlight: not found
/home/cameron/.profile: 11: s0_highlight_color: not found
/home/cameron/.profile: 12: s0_layout_mode: not found
/home/cameron/.profile: 14: [place]: not found
/home/cameron/.profile: 15: s0_workarounds: not found
/home/cameron/.profile: 16: s0_mode: not found
/home/cameron/.profile: 17: s0_position_matches: not found
/home/cameron/.profile: 18: s0_position_x_values: not found
/home/cameron/.profile: 19: s0_position_y_values: not found
/home/cameron/.profile: 20: s0_viewport_matches: not found
/home/cameron/.profile: 21: s0_viewport_x_values: not found
/home/cameron/.profile: 22: s0_viewport_y_values: not found
/home/cameron/.profile: 24: [decoration]: not found
/home/cameron/.profile: 25: as_shadow_color: not found
/home/cameron/.profile: 26: as_shadow_x_offset: not found
/home/cameron/.profile: 27: as_shadow_y_offset: not found
/home/cameron/.profile: 28: as_command: not found
/home/cameron/.profile: 29: as_mipmap: not found
/home/cameron/.profile: 30: as_decoration_match: not found
/home/cameron/.profile: 31: as_shadow_match: not found
/home/cameron/.profile: 33: [scale]: not found
/home/cameron/.profile: 34: Syntax error: redirection unexpected
```


I really don't know what to do with that. last time I just reinstalled, and I think Wolfram is getting sick of me reinstalling and asking for a new license key each time (about 10 times in the past 6 months)... so I don't care to reinstall. 

Any help is appreciated in advance. 

-aliencam

---

### Post by -grubby on 2007-11-27
You're PSU CAUGHT ON FIRE!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! That could cause serious hardware damage. I might suggest that you go to /home/[insert name here] and delete ./gnome (note that this deletes all your GNOME configuration though)

---

### Post by aliencam on 2007-11-27
well is there any way to back up some of  my gnome settings??? 

what kind of settings are we talking about deleting? just the eye candy and keyboard and mouse settings right?? 

then how do i restore the .gnome folder? or will it re-create itself on first login?

and yes, my PSU caught on fire while i was away for the weekend. I got a call form my roomate. surprised it didn't set off the dorm fire alarms, but they're 50 years old anyway.   really acrid smelling blacksmoke, and (when i turned it on when i got back to school) a "pop" like you hear when you microwave cheese too long... ugh.

---

### Post by aliencam on 2007-11-27
I tried deleting the /.gnome folder, and it didn't do anything.   I got a different process error number though, this time it is 
```
(process:15547): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:15551): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
```


anyone have any other ideas???

---

### Post by aliencam on 2007-11-27
I kept trying, and realised that every time i try to log in, even if i don't restart, the process ID changes.  because of this i don't know how to identify what process it is...

---

### Post by aliencam on 2007-11-28
I found this page:  [http://ubuntuforums.org/showthread.php?t=130892](http://ubuntuforums.org/showthread.php?t=130892)    but it doesn't show a solution.  it suggests that the person use "ps"  to see what the process is

here is my output of "ps" 


```
cameron@cameron-ubuntu-desktop:~$ ps
  PID TTY          TIME CMD
 8244 pts/0    00:00:00 bash
 8261 pts/0    00:00:00 ps
cameron@cameron-ubuntu-desktop:~$ 
```

I am in the failsafe gnome, and that output still doesn't have the numbers i'm looking for...

---

### Post by ruz322 on 2007-11-28
you may want to try booting into console only mode by using ctrl-alt-F1. try starting x. other than that I dont know a lot about the gnome error logs. or you could j ust try resintalling gtk and not gnome altogether. it looks like that is where the error is occuring.

---

### Post by aliencam on 2007-11-28
i can't find how to reinstall gtk, gtk2+ isn't in synaptic anywhere that I can find, so  i'm just going to reinstall things that use it: 

```
compiz (version 1:0.6.2+git20071119-0ubuntu1~gutsy1) will be re-installed
compiz-gnome (version 1:0.6.2+git20071119-0ubuntu1~gutsy1) will be re-installed
displayconfig-gtk (version 0.3.7) will be re-installed
gksu (version 2.0.0-4ubuntu2) will be re-installed
gtk2-engines (version 1:2.12.2-0ubuntu1) will be re-installed
gtk2-engines-pixbuf (version 2.12.0-1ubuntu3) will be re-installed
gtk2-engines-ubuntulooks (version 0.9.12-8) will be re-installed
```

---

### Post by aliencam on 2007-11-29
nothing I reinstalled from synaptic in the gnome failsafe did anything.  

How do i reinstall GTK?

---

### Post by zvacet on 2007-11-29
```
sudo apt-get --reinstall gtk
```

---

### Post by aliencam on 2007-11-29
> **zvacet said:**
> ```
sudo apt-get --reinstall gtk
```


That doesn't work either... I tried in the failsafe terminal and in gnome failsafe... 


```

cameron@cameron-ubuntu-desktop:~$ sudo apt-get --reinstall gtk
E: Invalid operation gtk
```

---

### Post by aliencam on 2007-11-29
i found out its 

```

sudo apt-get install --reinstall *package*

```

but "gtk" isn't a package... 


I'll try to reinstall: 

 libgtk2.0-0-dbg (version 2.12.0-1ubuntu3) will be installed
libgtk2.0-doc (version 2.12.0-1ubuntu3) will be installed
libio-stringy-perl (version 2.110-2) will be installed
libpod-escapes-perl (version 1.04-1) will be installed
libpod-simple-perl (version 3.04-1) will be installed
libgtk2-perl (version 1:1.140-1build1) will be re-installed
libgtk2.0-0 (version 2.12.0-1ubuntu3) will be re-installed
libgtk2.0-bin (version 2.12.0-1ubuntu3) will be re-installed
libgtk2.0-cil (version 2.10.2-1ubuntu2) will be re-installed
libgtk2.0-common (version 2.12.0-1ubuntu3) will be re-installed
libgtk2.0-dev (version 2.12.0-1ubuntu3) will be re-installed


using synaptic.

---

### Post by aliencam on 2007-11-30
reinstalling all of those did nothing as well.   I still get the same error: 

```
(process:5831): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:5835): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead.
```

i think i might start a new topic with the error as the title...



EDIT: 

i did start a new topic: 
[http://ubuntuforums.org/showthread.php?t=627339](http://ubuntuforums.org/showthread.php?t=627339)

and it is solved. 

To solve it, i simply reinstalled gnome. 

```
 sudo apt-get install --reinstall gnome
```

that worked to fix it. all it did bad was that it downloaded a bunch more packages to my computer (169MB). stuff like abiword, which I was debating installing anyway.

---

