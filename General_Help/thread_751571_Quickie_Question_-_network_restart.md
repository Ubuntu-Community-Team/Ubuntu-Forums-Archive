---
title: "Quickie Question - network restart"
date: 2008-04-10
forum: General Help
---

### Post by SteveHillier on 2008-04-10
I have just made changes to /etc/hosts as required by my Plesk server.

How can I restart the network serice without a cold restart of the machine.

There is a redhat command

/etc/init.d/network restart

THe must be an equivalent for Ubuntu.

Many thanks
Steve

---

### Post by bodhi.zazen on 2008-04-10
/etc/init.d/networking {start|stop|restart|force-reload}

tab completion is your friend here :twisted:

Did you change your hostname ? If so, you need also change /etc/hostname or you will lose access to sudo.

---

