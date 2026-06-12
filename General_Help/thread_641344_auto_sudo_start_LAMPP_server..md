---
title: "auto sudo start LAMPP server."
date: 2007-12-15
forum: General Help
---

### Post by odysseyes on 2007-12-15
hi,

I use a ubuntu PC as internal web server and now it's still standing on my desktop with keyboard and mouse, but I would like to put it on the attic together with out nas and other network stuff.

our network is sceduled to shut down at 2am and wake back up at 7am.

Now I need to start te server automatically with the command:
```
sudo /opt/lampp/lampp start
```

I can login standard with my created user automatically, but when I added an executable script with that line to sessions it still asks for a password, wich of course isn't very handy when you have a server running on your attic.

is it possible to send my root password with the command so that the command could be executed upon boot?

is there another option, like adding that line to the boot file?

i'm still new to linux so don't shoot me.. tnx for any help!

---

### Post by Linteg on 2007-12-15
I'm not really sure i know what you want to do, but If you want to automatically start and stop the service at specific times, you should write a cron script (there should be tutorials available). If you want it to start automatically as the computer boots, try looking in System->Admininstration->Services and see if what you want is there. If not, you can always (as root/superuser) edit /etc/rc.local and add the command there, above "exit 0" (everything in rc.local is run with root priviliges).

---

### Post by Josh1 on 2007-12-15
Write a shell script and put it into:
```
/etc/init.d/
```

Something like:
runlampp.sh
```
sudo /opt/lampp/lampp start
```
This will run it on boot.

edit:

Or you can try a cron task. I'm not sure exactly what timeframe you would use, but take a look at:
[http://www.adminschoice.com/docs/crontab.htm](http://www.adminschoice.com/docs/crontab.htm)

---

### Post by odysseyes on 2007-12-15
> **Linteg said:**
>  If you want it to start automatically as the computer boots, try looking in System->Admininstration->Services and see if what you want is there. If not, you can always (as root/superuser) edit /etc/rc.local and add the command there, above "exit 0" (everything in rc.local is run with root priviliges).
that's what I want since ourr network goes down with a timer.

I get the following error in terminal:
```
admin@SRVR01:~$ sudo edit /etc/rc.local
Warning: unknown mime-type for "/etc/rc.local" -- using "application/*"
Error: no "edit" mailcap rules found for type "application/*"

```

---

### Post by Linteg on 2007-12-15
Ah, I meant *edit*, the verb, try running ```
gksudo gedit /etc/rc.local
```

---

