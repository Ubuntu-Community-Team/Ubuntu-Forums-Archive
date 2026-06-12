---
title: "Stock at &quot;Setting up systemd&quot;  lib-init-rw.mount error"
date: 2015-10-10
forum: General Help
---

### Post by roadwarrior2 on 2015-10-10
I'm not sure what I did for this to happen but every time I try to install something now I get this error:

```
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
```

So then I run the command "sudo dpkg --configure -a" and then get this:

```
Setting up systemd (219-7ubuntu6) ...
Failed to stop lib-init-rw.mount: Unit lib-init-rw.mount not loaded.
```

And I cannot figure out what to do to get it to install programs again.

I read that this worked for most people

```
apt-get update
apt-get clean
apt-get autoclean
apt-get autoremove
apt-get check
apt-get -m update
apt-get dist-upgrade
```

But when I run the autoremove command it goes back to the systemd message.

```
Setting up systemd (219-7ubuntu6) ...
Failed to stop lib-init-rw.mount: Unit lib-init-rw.mount not loaded.
```

---

### Post by QDR06VV9 on 2015-10-10
Systemd is the active init system, switch to another like upstart and try again.
Via Reboot advanced options and choose upstart. I have to do this sometimes.
Regards

---

### Post by roadwarrior2 on 2015-10-10
I uninstalled upstart for some when I was drunk tought it was a good idea. I actually just got rid of the error with this command 

```
 sudo systemctl stop lib-init-rw.mount
```

---

### Post by QDR06VV9 on 2015-10-10
That's Great! Thanks for Sharing your fix.
Regards

---

