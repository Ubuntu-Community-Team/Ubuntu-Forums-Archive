---
title: "How do I change the Startup Applications of another user as root"
date: 2018-08-16
forum: General Help
---

### Post by webmiester on 2018-08-16
Hi everyone,

You might find this funny, and I hope someone can suggest something helpful...

First of all, I wanted to remap the cntr keys on my user account, so I added:
xmodmap -e "keysym Control_L = Scroll_Lock"
and 
xmodmap -e "keysym Control_R = Pause/Break"

to the application startup of the user.

I also removed all the menus on the gui, so that it will only boot up a browser.  So to do anything, I would open up a erminal and typr the commands there.

Something went wrong, and so now, when I open it up, the all the keys of the keyboard is messed up.  I cant open the startup applications menu on the terminal because the keyboard is all messed up.  I was hoping I can chenge the applications startup through from root.  Is there a way to do this?\
I looked up Alt-F2, and it brings up a list of applications, but the startup applications manager isnt one of them.  I cant type in the name of the manager into the box because the keyboard is messed up :(

Please help.  Thanks.

---

### Post by webmiester on 2018-08-16
by the way,

My root account isnt affected, 

 here is the output of the 

sudo -u <user> ls -al /etc/xdg/autostart
total 132
drwxr-xr-x 2 root root 4096 Aug  3  2017 .
drwxr-xr-x 5 root root 4096 Aug 27  2017 ..
-rw-r--r-- 1 root root  345 Apr 15  2016 a11y-profile-manager-indicator-autostart.desktop
-rw-r--r-- 1 root root  202 Feb 25  2016 at-spi-dbus-bus.desktop
-rw-r--r-- 1 root root  194 Mar 31  2016 blueman.desktop
-rw-r--r-- 1 root root  380 Dec  7  2016 deja-dup-monitor.desktop
-rw-r--r-- 1 root root  485 Nov  1  2015 gnome-keyring-pkcs11.desktop
-rw-r--r-- 1 root root  478 Nov  1  2015 gnome-keyring-secrets.desktop
-rw-r--r-- 1 root root  445 Nov  1  2015 gnome-keyring-ssh.desktop
-rw-r--r-- 1 root root  279 Nov 27  2015 gsettings-data-convert.desktop
-rw-r--r-- 1 root root  267 Jan 21  2017 indicator-application.desktop
-rw-r--r-- 1 root root  298 Apr  7  2016 indicator-sound.desktop
-rw-r--r-- 1 root root  246 Jan  4  2016 mate-maximus-autostart.desktop
-rw-r--r-- 1 root root 7454 Feb 11  2017 mate-power-manager.desktop
-rw-r--r-- 1 root root 5698 Feb 12  2017 mate-screensaver.desktop
-rw-r--r-- 1 root root 3018 Feb 12  2017 mate-settings-daemon.desktop
-rw-r--r-- 1 root root 8734 Jan 13  2017 mate-volume-control-applet.desktop
-rw-r--r-- 1 root root  350 Aug 26  2016 nm-applet.desktop
-rw-r--r-- 1 root root  289 Apr 18  2016 onboard-autostart.desktop
-rw-r--r-- 1 root root  301 Apr  8  2016 orca-autostart.desktop
-rw-r--r-- 1 root root 6479 Jan 13  2017 polkit-mate-authentication-agent-1.desktop
-rw-r--r-- 1 root root  375 Mar  8  2016 print-applet.desktop
-rw-r--r-- 1 root root 4474 Jan  6  2017 pulseaudio.desktop
-rw-r--r-- 1 root root 9344 Dec  9  2016 update-notifier.desktop
-rw-r--r-- 1 root root  312 Jul  3  2013 user-dirs-update-gtk.desktop

Can I just erase a line to fix it?  Specifically the lines which load the xmodmap.  I dont know which one it is on the list, and how do I disable it from here?  Thanks.

---

### Post by webmiester on 2018-08-16
I fixed it, but you might find my solution a bit funny...

I made my user account into an administrator account

From the terminal of my root account, I placed "su <user>"
then I ran sudo startup-applications-manager (or whatever it was called, since I changed it filename already)
it worked!  Thanks everyone

---

