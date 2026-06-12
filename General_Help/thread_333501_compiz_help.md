---
title: "compiz help"
date: 2007-01-07
forum: General Help
---

### Post by cptjaben on 2007-01-07
I've tried to install compiz using these methods:

[http://ubuntuforums.org/showthread.php?t=263840](http://ubuntuforums.org/showthread.php?t=263840)

[http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/](http://gandalfn.wordpress.com/howto/howto-compiz-aiglx-on-edgy/)

[http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide](http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide)

all 3 methods seem to get me in the same place. When i try to run GL desktop and click to enable it, all of my borders around my windows disappear as do my menu bars on the top and bottom of my desktop. However, when i turn it off everything turns back to nomral. I have an ATI card with 3d acceleration installed. anyone have any ideas?

---

### Post by Rich78 on 2007-01-07
That normally happens when it's first started up.

Have you rebooted since?

Have you applied it to a startup script?

Took me a bit of tweaking for it to work properly,  be careful though you can really bugger things up if you don't back up the conf files etc.

---

### Post by cptjaben on 2007-01-07
i haven't made a startup script, how do i go about making one?

---

### Post by Rich78 on 2007-01-07
This is for an Nvidia setup but this should be the same for the ATI.

If you create the script but don't apply it to the startup and try just running it from the terminal you'll know if it works or not.

Otherwise you may have problems disabling it if it messes up your GUI.

Try creating and running the script, then if that doesn't work just reboot the window manager by doing CTRL + ATL + Backspace.

IMPORTANT: Only apply it as a start up if you get it working correctly.

Taken from: [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Xgl.2FCompiz_.28Nvidia.29)

* Create a script that runs Xgl/Compiz on startup 

gksudo gedit /usr/bin/thefuture

* Insert the following lines into the new file. Replace .us with appropriate keyboard binding for your region. Eg .gb for United Kingdom. For a full list of keyboard bindings, type ls /usr/share/xmodmap in a terminal. If unsure, leave as .us (United States) 

#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
xmodmap /usr/share/xmodmap/xmodmap.us

    * Save the file 

sudo chmod 755 /usr/bin/thefuture

    * To run compiz for this session 

thefuture

    * To have compiz load on startup
          o System -> Preferences -> Sessions
          o Startup Programs -> Add 

/usr/bin/thefuture

    *
          o Click Ok, then Close

---

### Post by cptjaben on 2007-01-07
when i run the script it takes away all the window borders and top and bottoms from my desktop panel, the same way it does when i try and enable GL desktop. in the terminal it says:

/usr/bin/thefuture line 2: gnome-window-decorator: command not found.

Thanks for the help so far

---

### Post by Rich78 on 2007-01-07
I know I've come across this before, I really can't think what it is at the moment sorry.

I'll keep thinking though :-D

---

### Post by Rich78 on 2007-01-07
Try this:

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
sudo cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom-backup
gksudo gedit /etc/gdm/gdm.conf-custom

Replace the custom file with the following:

# GDM Configuration Customization file.
#
# This file is the appropriate place for specifying your customizations to the
# GDM configuration.   If you run gdmsetup, it will automatically edit this
# file for you and will cause the daemon and any running GDM GUI programs to
# automatically update with the new configuration.  Not all configuration
# options are supported by gdmsetup, so to modify some values it may be
# necessary to modify this file directly by hand.
# 
# To hand-edit this file, simply add or modify the key=value combination in
# the appropriate section in the template below.  Refer to the comments in the
# gdm.conf file for information about each option.  Also refer to the reference
# documentation.
# 
# If you hand edit a GDM configuration file, you should run the following
# command to get the GDM daemon to notice the change.  Any running GDM GUI
# programs will also be notified to update with the new configuration.
#
# gdmflexiserver --command="UPDATE_CONFIG <configuration key>"
#
# For example, the "Enable" key in the "[debug]" section would be specified by
# "debug/Enable".
#
# You can also run gdm-restart or gdm-safe-restart to cause GDM to restart and
# re-read the new configuration settings.  You can also restart GDM by sending
# a HUP or USR1 signal to the daemon.  HUP behaves like gdm-restart and causes
# any user session started by GDM to exit immediately while USR1 behaves like
# gdm-safe-restart and will wait until all users log out before restarting GDM.
# 
# For full reference documentation see the gnome help browser under
# GNOME|System category.  You can also find the docs in HTML form on
# [http://www.gnome.org/projects/gdm/](http://www.gnome.org/projects/gdm/)
# 
# NOTE: Lines that begin with "#" are considered comments.
# 
# Have fun!

[daemon]

[security]

[xdmcp]

[gui]

[greeter]

[chooser]

[debug]

[servers]# Override display 1 to use Xgl
0=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo 
flexible=true

-----------------------------------------

Now try your script again.

Good luck

---

### Post by kj1h234lkj1234 on 2007-01-07
I am having the exact same problem (gnome-window-decorator: command not found).

I followed the guide on ubuntuguide.org for XGL with an nVidia card, and also tried the suggestions here.

Any ideas?

This is a fresh install of 6.10 I am attempting to install it on

---

### Post by kj1h234lkj1234 on 2007-01-07
Nevermind, Beryl is much better and easier to use than Compiz. :D

---

### Post by costis on 2007-01-18
I located files containing the word decorator and found /usr/bin/gtk-window-decorator . I replaced it and now it works... "some how"... I 'll go for Beryl, and if it's stable enough I 'll keep it.

---

