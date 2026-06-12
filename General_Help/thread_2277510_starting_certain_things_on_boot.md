---
title: "starting certain things on boot"
date: 2015-05-09
forum: General Help
---

### Post by strange on 2015-05-09
i've just installed a server and i'm nearing completion but i still have a few small problems

1. i have installed an ftpd and it seems to only work when i run "sudo /etc/init.d/xinetd restart" after my system has completed booting.
i would like to find out why this is or a workaround would be if someone could tell me how to run that command automatically after boot

2. i would like my torrent client to start after i've started up in a tmux session i've made a simple file called "torrent" which i gave chmod +x i would like to know how to execute it after boot as well

all help would be greatly appreciated :)

---

### Post by ian-weisser on 2015-05-11
> **strange said:**
> 1. i have installed an ftpd and it seems to only work when i run "sudo /etc/init.d/xinetd restart" after my system has completed booting.
i would like to find out why this is or a workaround would be if someone could tell me how to run that command automatically after boot
The specific answer to your question is "Most likely your ftpd is trying to start too early in the boot process."
Using xinetd is itself a workaround - both Upstart (Ubuntu 14.10 and earlier) and systemd (Ubuntu 15.04 and later) have that functionality baked-in now. 
See [http://upstart.ubuntu.com/cookbook/](http://upstart.ubuntu.com/cookbook/) for Upstart.
See [http://0pointer.de/blog/projects/socket-activation.html](http://0pointer.de/blog/projects/socket-activation.html) for systemd.

Alternately, if you want ftpd to really run as an always-on daemon, the right way is to create (or edit) an Upstart .conf or systemd .wants file so ftpd starts at the appropriate time during boot..


> **strange said:**
>  2. i would like my torrent client to start after i've started up in a tmux session i've made a simple file called "torrent" which i gave chmod +x i would like to know how to execute it after boot as well

Most Ubuntu torrent daemons -including Transmission and Deluge- run headless - they do not need to be tmux-ed. Simply start them at boot like other headless system services, and open/close a client as needed to control and monitor them. Clients can be GUI, web-based, or command-line. Best practice is to run internet-facing services, including torrent daemons as a separate 'system' user, never as root nor you.

Some utorrent-based torrent applications do need to be tmux-ed...because the daemon and the client run in the same application. These cannot be run at boot without considerable kludging - they require a display (which doesn't exist before a human logs in) to work. These can be easily started after login - place a script in your Startup Applications dir. It's unwise practice - the internet-facing application will run as you. If the application is ever compromised, your data will be at risk.

---

