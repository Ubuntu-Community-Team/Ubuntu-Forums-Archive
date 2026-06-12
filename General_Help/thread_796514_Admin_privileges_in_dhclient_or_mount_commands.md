---
title: "Admin privileges in dhclient or mount commands?"
date: 2008-05-16
forum: General Help
---

### Post by tr0k0l0 on 2008-05-16
Hi, i´ve got a question please...

When i try  a dhclient, ifconfig or mount command on a shell, i am asked for the admin password, thats ok.. but however there are some  apps like nm-applet or gnome-volume-manager (both run when i log into session) that do the same and no password is requiered... why is does this happen?

For example, when i login in fluxbox environment, gnome-volume-manager is not launched and if i want to mount a pendrive, i´ve to make it as root and therefore everything on that unit has to be made as root, (copying, moving, creting anything)...thats very tedious.

Thanx very much...

---

### Post by Monicker on 2008-05-16
Normal users should not be able to alter the network connectivity or the file system of a machine.  Remember, unix and linux were designed as multi user systems, even though many may not be using them as such.  Would you want your friend John, who is remoted in, to change the ip address of your network card and cut you off from the network?  :)

---

### Post by tr0k0l0 on 2008-05-16
no. i wouldn´t but i neither  would like that john would come to have a coffee at home and do the same cutting off my connexion just going to the network manager and turning the network off..(without been asked for a root password) :-(

---

### Post by Monicker on 2008-05-16
If you are not physically at your system, and you have people around that you can not trust, then you should lock your desktop.  I always do that.  I learned that lesson a long time ago when doing tech support for an isp.  If you ever got caught leaving your shell account open and were away from your desk, there would be some very interesting surprises for you when you got back.

---

### Post by tr0k0l0 on 2008-05-16
Ok nice advice, thank you very much but i wonder about the same.... is there a way of changing for example, network or mounting options without been asked for root password like nm-applet or gnome-volume-manager do?

---

### Post by Monicker on 2008-05-16
You can modify /etc/sudoers, and specify commands which do not require a password to be entered.  For the sake of security you should define these exceptions as narrowly as possible.

[https://help.ubuntu.com/community/Sudoers]("https://help.ubuntu.com/community/Sudoers")

For example, the following would allow the use of SomeCommand without being asked for a password.

```
username ALL=(ALL) NOPASSWD: /bin/SomeCommand
```

Or, for anyone in the admin group

```
%admin ALL=(ALL) NOPASSWD: /bin/SomeCommand
```


You can find the path to a command using which.

```
which dhclient
```

---

### Post by tr0k0l0 on 2008-05-16
ok, thank you very much, but i would like to know why gnome-volume-manager is able to mount without any password and without editing anything in anywhere, as well as network-manager is able to change my network configuration without giving a password...

---

### Post by Monicker on 2008-05-16
Those applications may be setuid root.  Meaning that they have root privileges no matter who runs them.  I'm not in a position to verify that at the moment, but that is not an uncommon way to handle it, though it can potentially be security risk.

---

