---
title: "PHP upgrade"
date: 2008-02-27
forum: General Help
---

### Post by somethingobscure on 2008-02-27
Hi, I'm fairly new to linux - I've just built an Ubuntu 6.06 LAMP server as my first linux build ever. It's all set up and works fine and I'm very chuffed with myself. (I did cheat by going down the GUI route and then using command line to install AMP, but I tried LAMP first and failed!) I'm using the box to develop a web application that uses the Google Gdata API library. This contains a function that was released with PHP 5.1.3 but I've got 5.1.2! Oh no!

How do I go about upgrading PHP. I have no problems updating to 5.2.3 if that's easiest, as long as I get my function calls!

Thank-you! :D

---

### Post by keenboy on 2008-02-27
try

sudo apt-get -s install php5

This will simulate the installation and will tell you if an upgrade is available. If it says it is the newest version you may need to look at adding some extra repositories or building php from source.

---

### Post by az on 2008-02-27
Dapper will not use any other version of php.  If you need a later version, dist-upgrade to a new version of Ubuntu.

You would probably be able to dist-upgrade to Hardy without a problem.  If you encounter any problems, start from a fresh install.

If this is for a production system, use Gutsy and then dist-upgrade to Hardy when it releases.

---

### Post by somethingobscure on 2008-02-27
Thanks for the advice. The server's running my uni final year project so I would like it to be stable! How would I go about upgrading? I've tried sudo apt-get dist-upgrade but I just get:

```
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by az on 2008-02-27
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

If you just started out, though, it would be easier to just download the 7.10 iso and install fresh.  Dist-upgrading from Dapper to Hardy will be supported, but dist-upgrading from Dapper to gutsy is not, since gutsy is not a LTS release.

---

### Post by somethingobscure on 2008-02-28
Thanks again. I've started a clean install. Thankfully I'm using VMWare so it does at least mean that I can keep the first one live until this is ready! :)

---

### Post by az on 2008-02-28
> **somethingobscure said:**
> Thanks again. I've started a clean install. Thankfully I'm using VMWare so it does at least mean that I can keep the first one live until this is ready! :)

If you want it to be stable, avoid vmware.

---

