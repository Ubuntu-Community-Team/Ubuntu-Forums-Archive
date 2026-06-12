---
title: "error &quot;Your session lasted less than 10 seconds&quot;"
date: 2007-10-07
forum: General Help
---

### Post by [alterego] on 2007-10-07
Yet another thread about the error "your last session lasted less than 10 seconds"..
Any ideas as to what I can do to stop this error from popping up again and again?

This is the details I get:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "berggreen"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Ubuntu-3Ghz:/tmp/.ICE-unix/6019
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

(update-notifier:6089): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-cups-icon:6094): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.

(gnome-power-manager:6088): GnomeUI-WARNING **: While connecting to session manager:
IO error occured opening connection.



I've read other threads about this problem - none of the suggestions helped me.
I haven't deleted my /tmp .. -or anything in it.
Please help me understand the details in this error.

Computer: Intel Celeron 3 Ghz, 100 gb. hdd, 768 mb. RAM, Ubuntu Feisty Fawn, Gnome.

---

### Post by elijathegold on 2007-10-07
I got this error after installing a new distro, using the same using the same user name as my
previous distro and keeping the home directory. 

The way to fix it in this situation is make sure you have permissions to your home directory.

Boot to a command console, log in as root and then use this command


chown -R yourUserName: /home/your-home-directory/

---

