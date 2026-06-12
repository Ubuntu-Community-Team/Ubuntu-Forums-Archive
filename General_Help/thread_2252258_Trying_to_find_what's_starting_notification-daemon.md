---
title: "Trying to find what's starting notification-daemon"
date: 2014-11-10
forum: General Help
---

### Post by schwim-dandy on 2014-11-10
Hi there folks, 

I've got a  Ubu 14.10 minimal install with Openbox.  notification-daemon is crashing consitantly and finding many Google results pointing to the Ubu bugtracker where users are enjoying the same undocumented feature.  Being of the mindset that if I can't beat it, disable it, I'd like to .... disable it.  The only issue is that I can't seem to find where it's being started.  I've checked /usr/share/dbus-1/services, /etc/init.d/ and /etc/rc1-6.d.  I've checked with rcconf and sysv-rc-conf.  I can't mention of it  anywhere. I'm not using a DM at all.  I edited tty1.conf to log in automatically,  then created a bash_profile to have it startx immediately upon login.

Could someone point me toward the location of the startup?  Thanks for your time!

---

### Post by ajgreeny on 2014-11-10
Maybe it is **/etc/xdg/autostart/gdu-notification-daemon.desktop** which is where it is in my Xubuntu 12.04 system.

Try renaming that file as a backup, or open it in a text editor and comment out the Exec= line

You could also try removing the execute permissions of the daemon with ```
sudo chmod -x /usr/lib/gnome-disk-utility/gdu-notification-daemon
```

PS: I have not tried any of this, so proceed with some caution.  However, if it all goes wrong you can easily reverse both of those actions.

---

### Post by schwim-dandy on 2014-11-12
Thanks very much for your help.  I commented the execute line and all seems quiet now.

---

