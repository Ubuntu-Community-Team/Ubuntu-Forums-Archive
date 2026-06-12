---
title: "Apache help"
date: 2007-06-03
forum: General Help
---

### Post by macmichael01 on 2007-06-03
Hello for some reason I have apache1.3 and apache2 installed and for some reason it defaults to apache1.3.  I would rather have apache2 running but I don't know how to tell ubuntu to use apache2 instead of apache1.3. I tried uninstalling apache1.3 and starting up apache2 and it does not indicate that it has even started from the command line. Any suggestions as to why this has defaulted to apache1.3 and why I cannot use apache2?

---

### Post by Beamerboy on 2007-06-03
Try the following form a terminal:

```

sudo /etc/init.d/apache stop

```

then type:

```

sudo /etc/init.d/apache2 start

```

Hope that helps,

Paladine

---

### Post by macmichael01 on 2007-06-03
well that's what I meant when I said did not see anything from the command line that indicated that apache has started.

chris@gertrude:~$ sudo /etc/init.d/apache2 start
chris@gertrude:~$ 

there should a line stating that apache started, stopped, restarted or error'd out. I would think there would be some kind of configuration file somewhere that tell ubuntu which apache version to us as apposed to defaulting to apache1.3. even when I remove apache1.3 it does nothing.

---

### Post by Beamerboy on 2007-06-03
Type:

```

ps aux | grep apache

```

That should list all the httpd children.  For apache 2 it should give a bunch of lines that look like this:

www-data  6468  0.0  0.2  37664  6068 ?        S    Jun03   0:00 /usr/sbin/apache2 -k start

If you are using apache 1.3 then it will say something other than apache2

If this confirms you are not using Apache2 you might want to `sudo apt-get remove --purge apache1.3` or whatever the package is called.  That should remove all traces of Apache 1.3 from your system but it might remove some dependencies needed by other packages (such as Apache2) so make sure you take a note of the dependencies it removes so you can reinstall them if needed.  Would probably help to do a reinstall of Apache2 once you have purged Apache 1.3

Hope that helps

Paladine

---

### Post by macmichael01 on 2007-06-03
well this is what it returns which I have no idea what any of that means.

root@gertrude:/home/chris# ps aux | grep apache
root      4937  0.0  0.0   2884   752 pts/0    R+   22:03   0:00 grep apache
root@gertrude:/home/chris# 

thanks for helping me.

---

### Post by Beamerboy on 2007-06-03
> **macmichael01 said:**
> well this is what it returns which I have no idea what any of that means.

root@gertrude:/home/chris# ps aux | grep apache
root      4937  0.0  0.0   2884   752 pts/0    R+   22:03   0:00 grep apache
root@gertrude:/home/chris# 

thanks for helping me.

Well according to your process list apache isn't running at all.  Try just reinstalling apache2 and see if that fixes it.

Paladine

---

### Post by macmichael01 on 2007-06-03
ok I  ran this command dpkg --list *apache* and found that there were a few apache things installed.  I removed the rest of the apache stuff and then installed the apache2 stuff and still nothing happens. when I type /etc/init.d/apache2 start

---

### Post by macmichael01 on 2007-06-04
I am still needing help on this issue. I talked with several other people and I can't seem to find out what is wrong. Help please!

---

### Post by macmichael01 on 2007-06-04
IS any one out there?? Hello!

---

