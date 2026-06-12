---
title: "create privileged account [Resolved]"
date: 2007-04-11
forum: General Help
---

### Post by panda726 on 2007-04-11
I am locked out of my privileged account by changing the home directory to one on a fat32 partition.  I do know the root password, but I cannot figure out how to create another privileged user with which to change the setting back, or change it back through the command line.

When I attempt to login, I get the message:

> 
Your home directory is listed as:
'/sda2/xyz'
but it does not appear to exist.  Do you want to log in with the /
(root) directory as your home directory?

It is unlikely anything will work unless you use a failsafe session.


Clicking on the OK button gives me the message that

> 
User's $HOME/.dmrc file is being ignored.  This
prevents the default session and language from being
saved.  File shoud be owned by user and have 644
permissions.  User's $HOME directory must be owned
by user and not writable by other users.


Clicking again on OK, I am notified that my session lasted less than 10 seconds, and it is suggested that I login with one of the failsafe sessions.  The ~/.xsession-errors file is as follows:

> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm:/0.Xservers" -h " " -l ":0" "[loginname]"
/etc/gdm/Xsession: Beginning session setup...

(gnome-session:4912: libgnomevfs-WARNING **: unable to create ~/.gnome2 directory: No such file or directory
Could not crote per-user gnome configuratio directory '/sda2/xyz/.gnome2/": No such file or directory


Any help on this would be much appreciated

---

### Post by aysiu on 2007-04-11
Try rebooting into recovery mode. More details here:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

Alternatively, you can boot the Desktop CD (or live CD), mount your Ubuntu partition, edit the /etc/fstab back, and then see if that fixes your problem.

---

### Post by panda726 on 2007-04-11
Aloha aysiu,

Thank you for the easy to follow instructions.  Everything seems to work as it should now.

Tor

---

