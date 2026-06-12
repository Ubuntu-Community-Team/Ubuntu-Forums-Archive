---
title: "How do I have a service started automatically on bootup"
date: 2008-01-19
forum: General Help
---

### Post by s|k on 2008-01-19
I have services/apps such as bitlbee (an im client and irc server in one) and ddclient (a dyndns update service client) that I have to start each time I reboot. Given that computers are all about automation there must be some way to have these things started by default. I've tried to search around and have found nothing, only other people asking the same thing with not a lot of answers. Anyone know or will this be another one of these unanswered questions of the same nature?

Thanks a bunch.

---

### Post by ugm6hr on 2008-01-19
Are you in Xubuntu or Ubuntu?

From memory :

In Xubuntu - there is an Autostarted Applications program mamager.

In Ubuntu - there is a Sessions manager

Both allow you to add programs to be autostarted on booting.

---

### Post by peabody on 2008-01-19
You can place commands you wish to run on boot in the /etc/rc.local file.

gksu gedit /etc/rc.local

Be sure to leave that exit 0 at the bottom of the file.  I also recommend using absolute paths to the executables you wish to run (i.e. /usr/bin/ddclient).

One thing to be very careful of is that anything run from this file will be run as root.  Since you mentioned running something via IRC, that could be dangerous.  You could use the "su" command to drop privileges to a specific user account.

su username -c 'command goes here'

If you wanted to run something from that file that you could then later reconnect to, I recommend running the program via a detached screen:
su username -c 'screen -d -m command to run goes here'

Then you may connect the file by using "screen -r" from a terminal.  Ctrl+A d to detach from the screen again.

---

