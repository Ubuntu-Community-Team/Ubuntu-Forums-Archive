---
title: "Can't use apt-get"
date: 2012-11-08
forum: General Help
---

### Post by CharlyZA on 2012-11-08
When I use apt-get I get this error: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. I want to install GD for my web server. I used sudo apt-get install php5-gd This happens with all apt-get commands. Thanks

---

### Post by grahammechanical on 2012-11-08
You do not say if you followed the instructions in that error message. Did you run?

```
sudo dpkg --configure -a
```

---

### Post by Slim Odds on 2012-11-08
> **CharlyZA said:**
> When I use apt-get I get this error: dpkg was interrupted, [SIZE=4]you must manually run [/SIZE]'sudo dpkg --configure -a' to correct the problem. I want to install GD for my web server. I used sudo apt-get install php5-gd This happens with all apt-get commands. Thanks
That message is there for a reason.

---

### Post by CharlyZA on 2012-11-09
I have tried. I get this error:
```

root@CFP:~# sudo dpkg --configure -a
Setting up proftpd-basic (1.3.4~rc2-4) ...
cp: cannot create regular file `/etc/proftpd/proftpd.conf.proftpd-new': No such file or directory
dpkg: error processing proftpd-basic (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 proftpd-basic

```

---

### Post by ibjsb4 on 2012-11-09
You say that it happens with apt-get commands.  Makes me wonder if you need to update.

sudo apt-get update

Then try an install

---

