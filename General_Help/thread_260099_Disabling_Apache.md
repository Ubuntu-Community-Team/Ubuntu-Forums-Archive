---
title: "Disabling Apache"
date: 2006-09-18
forum: General Help
---

### Post by Lunar_Lamp on 2006-09-18
Ubuntu comes with apache installed by default, and whilst I don't care about it, I know that it's doing something in the background as I recollect seeing it report messages on boot/shutdown.  I am fairly sure that it's just saying "no can do, you haven't configured me", but I can't be sure as I've never had cause to use it, and don't have a clue about apache.  I suspect that it is disabled by default, however, just checking out the rules for my uni network when I go back, I saw this:

> Can I connect my Apple Mac / Linux machine / Commodore 64?

Yes, as long as it supports TCP/IP, DHCP and has a Web browser for the registration process.

Some operating systems come with servers installed by default (eg web servers on Linux). These must be disabled before you connect to the service.

So, er, how do I disable apache if it's enabled?  I presume they are just saying it's not allowed, but I'd like to stay within the rules.  Will disabling it affect any other packages?  How can I check?

This may be of use:

```
$ ps aux | grep apach
root      5829  0.0  0.4  13200  4140 ?        Ss   13:09   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5868  0.0  0.2  13328  2384 ?        S    13:09   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5869  0.0  0.2  13328  2384 ?        S    13:09   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5870  0.0  0.2  13328  2384 ?        S    13:09   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5871  0.0  0.2  13328  2384 ?        S    13:09   0:00 /usr/sbin/apache2 -k start -DSSL
www-data  5872  0.0  0.2  13328  2384 ?        S    13:09   0:00 /usr/sbin/apache2 -k start -DSSL
ed       13380  0.0  0.0   2888   812 pts/0    R+   15:41   0:00 grep apach

```

---

### Post by kidders on 2006-09-18
Yep ... your web server's running alright. Afaik **/etc/init.d/apache2 stop** is enough to kill it, while leaving it installed.

As far as effects on other apps go, they would be obvious to you, in that none of your web-based applications (like phpmyadmin) would run any more.

There is one other alternative you may not have considered, which would allow you to continue using apps that require apache. (Again, if you've installed one, you'll know it!) You *could* use your firewall to explicitly block all non-local connections to your web server, or expressly forbid apache to bind to any network interfaces other than your loopback. This would have the effect of preventing you from serving any content to your college network (the reason for the ban) and render your web service externally undetectable.

---

### Post by Lunar_Lamp on 2006-09-19
So, a temporary solution would be to add "/etc/init.d/apache2 stop" to my startup routine, and see if it affects anything?

Or does using the stop command on apache2 stop it until explicitely restarted (despite a reboot)?

---

### Post by dmizer on 2006-09-19
depending on your gui manager, you should be able to turn apache off completely.  something about services?  i wasn't aware that apache was preinstalled now.  i've always had to install it manually after installing ubuntu.  course, i generally do the alternate install to cli only anymore.

edit to add:
no, stoping it is not persistent.  it will turn back on next time you reboot.

---

### Post by Ramses de Norre on 2006-09-19
```
sudo aptitude install sysv-rc-conf
sudo sysv-rc-conf
```

Go down to apache's line and disable it for runlevel 2 (with the space bar).
Press 'q' to quit. Now apache wont start on boot up nomore.

---

### Post by Lunar_Lamp on 2006-09-19
Thanks!  I knew there would be a simple way to do it.

---

### Post by twowheeler on 2006-09-19
> **Lunar_Lamp said:**
> Ubuntu comes with apache installed by default, <snip>


I don't think so.  It certainly is not installed on any of my systems.  You might have installed a package with a dependency on apache which pulled it in.  You could remove apache and see what happens.  If something breaks, put it back.  At least you would know how it got there, and you might decide you don't need any of these packages.

---

