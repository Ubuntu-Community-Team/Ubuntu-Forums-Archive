---
title: "'warning: could not initiate dbus' - update-manager"
date: 2007-01-12
forum: General Help
---

### Post by jaakan on 2007-01-12
Does anyone have any ideas on hunting down the bug for this?

---

### Post by gaitanis on 2007-01-29
Same problem. Here is the exact output of the update-manager when trying to download the updates :

kosta@gaitanis-laptop:~$ sudo update-manager
Password:
warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

At the end the update-manager does not install anything... However, by doing apt-get upgrade everything works correctly

Any ideas?

---

### Post by spottraining on 2007-03-03
same problem here.

Ubuntu 6.10.
I wnat to upgrade to Festy, but no luck - still I get "Your System is up-to-date" message. Even, when I start update-manager from terminal, with command:
sudo update-manager -d
or
gksu "update-manager -d" 

still nothing....

---

### Post by andrew.46 on 2007-03-04
Hi,

 Normally I don't reply to posts like this with "me too":

> **jaakan said:**
> Does anyone have any ideas on hunting down the bug for this?

 But this is affecting me too. Trying to upgrade to Feisty. Most exasperating,

                               Andrew

---

### Post by zorkerz on 2007-03-25
Yep i simply get this > gksu "update-manager -d"
warning: could not initiate dbus
has anyone filed or found a bug for this or some idea what is causing it?

---

### Post by rojanu on 2008-02-05
I am trying to upgrade to hardy and the upgrade just dies without any error message
> $ gksudo "update-manager -c -d"
warning: could not initiate dbus
extracting '/tmp/tmpnPoeja/hardy.tar.gz'
authenticate '/tmp/tmpnPoeja/hardy.tar.gz' against '/tmp/tmpnPoeja/hardy.tar.gz.gpg'

---

### Post by MatthiasHeil on 2008-03-15
same here

---

### Post by optimusmedia on 2008-03-20
Happy Beta Day.  However, I'm having this error too.  

```
$ sudo update-manager -d
warning: could not initiate dbus
extracting '/tmp/tmpfvyDTp/hardy.tar.gz'
authenticate '/tmp/tmpfvyDTp/hardy.tar.gz' against '/tmp/tmpfvyDTp/hardy.tar.gz.gpg'
```

And there it hangs.](*,)

---

### Post by cristiantm on 2008-03-26
Same here too, when trying to update to hardy... any solution?

---

### Post by cristiantm on 2008-03-26
Just to let you know. Running it *realy* as root works fine!

* CTRL+ALT+F1
* login as your user
* sudo su -
* startx -- :1
* open an terminal and run update-manager -d

---

