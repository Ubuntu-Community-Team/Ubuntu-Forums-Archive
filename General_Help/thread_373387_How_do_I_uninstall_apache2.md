---
title: "How do I uninstall apache2?"
date: 2007-03-01
forum: General Help
---

### Post by Valiante on 2007-03-01
I installed Apache2 and Webmin to get my web server up and running but have since taken advice to use lighttpd instead.

How do I remove apache2 (assuming I need to) and webmin, or at the very least stop them from starting/running ?


Valiante

---

### Post by taurus on 2007-03-01
```
sudo aptitude --purge remove apache2 webmin
```

---

### Post by Valiante on 2007-03-01
```
# aptitude --purge remove apache2 webmin
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

Does that mean it did/didn't work? :confused:

---

### Post by Valiante on 2007-03-03
Sorry to bug you guys but I still can't get rid of apache2.  If for some reason I take my machine down, when it boots back up apache loads over lighttpd - how can I stop this?

Please bear in mind I'm very new to Linux...

---

### Post by scxtt on 2007-03-03
you can remove /etc/init.d/apache2 (or delete the sym link in /etc/rc*.d that points to it

* = the run-level you use (who -r will tell you)

---

### Post by Valiante on 2007-03-03
And to do that I use the update-rc.d command?

Sorry, I'm really new to all this.  Where's a registry when you need it? :p

---

### Post by Valiante on 2007-03-03
It's ok I think I figured it out...

```
sudo update-rc.d -f apache2 remove
```

---

