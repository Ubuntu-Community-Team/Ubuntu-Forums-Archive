---
title: "Only Failsafe Gnome Works"
date: 2007-09-17
forum: General Help
---

### Post by taekwondodogoof on 2007-09-17
Hi,
             I recently upgraded to Gutsy, and it worked for a while. Then, there was a whopping upgrade day a few weeks ago, and I upgraded everything. When I restarted, I could not log into my Gnome desktop. I would get that tan screen with my cursor in it. (Sometimes after a few minutes it'll boot me back to start up scripts and take me to login screen.) I can move my cursor, but I can't bring up Ctrl-Alt-F1 or any of those. THe only thing I can do is Ctrl-Alt-Del, and go back to the log-in screen. I can log in perfectly with Gnome failsafe.

               Any helps appreciated!
                        Thanks everybody :)!


Here's my xsession-errors file
```

(process:7868): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:7872): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: present. 
Starting Xgl with options:  -accel xv:fbo -accel glx:pbuffer -fullscreen -br/etc/X11/Xsession.d/00xserver-xgl_start-server: 100: Xgl: not found
xmodmap:  unable to open display ':1'
xrdb: Connection refused
xrdb: Can't open display ':1'
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
/usr/bin/xmodmap:  unable to open display ':1'
```

---

### Post by Digitallysick on 2007-09-17
try sudo dpkg-reconfigure xserver-xorg

---

### Post by burningbed on 2007-10-21
I have had somewhat similar problems (see [http://ubuntuforums.org/showthread.php?t=583642]("http://ubuntuforums.org/showthread.php?t=583642")) and they were all solved by uninstalling xserver-xgl.
I'd try running running apt-get remove xserver-xgl and see if it helps.

---

### Post by daveska on 2007-11-09
> **taekwondodogoof said:**
> Hi,
             I recently upgraded to Gutsy, and it worked for a while. Then, there was a whopping upgrade day a few weeks ago, and I upgraded everything. When I restarted, I could not log into my Gnome desktop. I would get that tan screen with my cursor in it. (Sometimes after a few minutes it'll boot me back to start up scripts and take me to login screen.) I can move my cursor, but I can't bring up Ctrl-Alt-F1 or any of those. THe only thing I can do is Ctrl-Alt-Del, and go back to the log-in screen. I can log in perfectly with Gnome failsafe.

               Any helps appreciated!
                        Thanks everybody :)!


Here's my xsession-errors file
```

(process:7868): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.

(process:7872): Gtk-WARNING **: This process is currently running setuid or setgid.
This is not a supported use of GTK+. You must create a helper
program instead. For further details, see:

    http://www.gtk.org/setuid.html

Refusing to initialize GTK+.
/etc/gdm/Xsession: Beginning session setup...
Checking for nVidia: present. 
Starting Xgl with options:  -accel xv:fbo -accel glx:pbuffer -fullscreen -br/etc/X11/Xsession.d/00xserver-xgl_start-server: 100: Xgl: not found
xmodmap:  unable to open display ':1'
xrdb: Connection refused
xrdb: Can't open display ':1'
/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found
/usr/bin/xmodmap:  unable to open display ':1'
```


hey im fairly new to ubuntu, ive had it for about 2 weeks now , and i think its an amazing os, my only real troubling issue so far was getting compiz to work, i abandoned that project for now, but somewhere when i was messing with compiz, i screwed up my ubuntu and i get the same error message as the one above when trying to log into xclient or gnome, except when it comes to the ect/gdm it doesnt start it up, and it says it cant open file " /etc/ati/ati-fglrx-.sh, and i have looked for the file its not there, so i cant understand why its trying to open it up, any help would be greatly appreciated

oh by the way, id like to know how your getting the error file, i tried to copy it and nothing, noob question i know, but like i said fairly new

---

### Post by Endolith on 2007-12-14
Try renaming ~/.gnome2/session to something else.

---

### Post by marsplus on 2008-01-23
I had the same problem

as you suggested, I renamed the session file ... and it worked!!!

Thanks Endolith

:guitar:

---

### Post by uptimebox on 2008-04-28
> **Digitallysick said:**
> try sudo dpkg-reconfigure xserver-xorg

The same problem with "Stable" 8.04 release on Asus X51R + Radeon XPRESS 200M was solved by removing xserver-xgl package.

UPDATE:

And xorg-driver-fglrx had to be installed.

---

### Post by Endolith on 2008-04-28
> **marsplus said:**
> I had the same problem

as you suggested, I renamed the session file ... and it worked!!!

I had to do this yesterday again, in Hardy.  I don't see any reason why this should be necessary.  Certain processes should always start when you start gnome, like the panel.  For me, the session gets screwed up due to NX starting multiple sessions on the same computer, and the programs don't want to run twice.

---

