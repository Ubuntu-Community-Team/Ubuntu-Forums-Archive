---
title: "Xsession Problem"
date: 2007-03-17
forum: General Help
---

### Post by escobar5 on 2007-03-17
Hello,

im having a problem with the gnome session of one of the users of my ubuntu, it log out just before i log in, and i see a message that says that something happen with the xsession so i check the xsession-errors.log file and it have this:

```

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "escobar5"
/etc/gdm/Xsession: Beginning session setup...
/etc/profile: 21: [[: not found
SESSION_MANAGER=local/escobar5-desktop:/tmp/.ICE-unix/6568
Xsession: X session started for escobar5 at Fri Mar 16 19:01:00 COT 2007
SESSION_MANAGER=local/escobar5-desktop:/tmp/.ICE-unix/6689
Initializing gnome-mount extension
** Message: failed to load session from /home/escobar5/.nautilus/saved-session-KQ2EPT
Starting Azureus...
Java exec found in PATH. Verifying...

** (nautilus:6786): WARNING **: Can not caclulate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6786): WARNING **: Can not calculate _NET_NUMBER_OF_DESKTOPS

** (nautilus:6786): WARNING **: Can not get _NET_WORKAREA

** (nautilus:6786): WARNING **: Can not determine workarea, guessing at layout
** Message: drive = 0
** Message: volume = 0
** Message: drive = 0
** Message: volume = 0
** Message: drive = 0
** Message: volume = 0

(gnome-power-manager:6795): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6796): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.
Session management error: IO error occured opening connection

(update-notifier:6814): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:6815): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:6812): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(beryl-manager:6835): Gtk-WARNING **: cannot open display:  

```

I am in ubuntu feisty and this problems happened after some updates.

Any help would be greatly appreciated.

Thanks in Advance

Escobar5

---

### Post by escobar5 on 2007-03-17
Also, when i log in with a different user after trying to log in with my user i see that my cpu is 100%, when i look at the processes i see a lot of xrdb zombies

---

### Post by peabody on 2007-03-17
you might want to a do a search for files in the user's folder called .ICE*.  I don't know what that folder's for, but I've had problem with it in the past.  Zapping it seemed to solve the problem.  The safer bet is to move it somewhere else first.

---

### Post by escobar5 on 2007-03-20
Ok thanks for your replies,

I fixed the problem by deleting the folders .gnome, .gnome2 and .gconf,

but now i see something, when i change my splash image the problem appears again,
and then i delete the splash and the problem goes away,

any ideas?

---

### Post by Sentai on 2007-05-29
escobar5! How did you find these "dot" files? .gnome, .gnome2 and .gconf,

When you delete them what happened after that? Did you just reboot? You see I have this same problem and it´s driving me grazy!

Hopefully there is some reasonable solution for this one... Newbies like me it can be  really painfull to solve this without any help :D

---

### Post by fanatik on 2007-05-29
these are 'hidden' files in your home directory. you can see them if you open a terminal and type:

```
$ ls -la
```

hope that helps.

---

### Post by Sentai on 2007-05-29
Thanks fanatik! If I remove these hidden files or dir´s (mentioned above) what happens then?

It seems to be that I have problem with "connection session manager"?? There are several error messages related on different kind of session manager actions... see listing below

--------------------------------------------------------------------------------------------------------------------------------
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mikko"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mikko-desktop:/tmp/.ICE-unix/10576

(gnome-session:10576): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field


(gnome-panel:10642): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

Initializing gnome-mount extension

(nautilus:10641): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field


(gnome-cups-icon:10648): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(evolution-alarm-notify:10653): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:10654): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-terminal:10654): Gtk-WARNING **: Theme directory 48x48/mimetypes of theme Snow-Apple has no size field

evolution-alarm-notify-Message: Setting timeout for 7116 1180213200 1180206084
evolution-alarm-notify-Message:  Sun May 27 00:00:00 2007

evolution-alarm-notify-Message:  Sat May 26 22:01:24 2007


(gnome-power-manager:10645): GnomeUI-WARNING **: While connecting to session manager:
IO error occured doing Protocol Setup on connection.

(update-notifier:10646): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

---

### Post by Sentai on 2007-05-30
Great! Actually I managed to get rid of this problem so far! 

I removed (to another location) nearly all "dot" files and folders. After restart problem disappeared but I lost all my previous configurations... Desktop backround, themes and so on.

However when I returned some of the old .files back in order to find out where the real problem was. I wasn´t able to recover my old configuration back? Have anyone any idea which are the files or folder that affects ones Desktop setup?

Anyway I´m relief that this really annoying problem is gone so far....

---

