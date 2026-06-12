---
title: "Start GUI app from script"
date: 2007-02-12
forum: General Help
---

### Post by akosh on 2007-02-12
Hi,

I have an Ubuntu server with Openbox and Firefox used in a hall for displaying information.
I would like to restart Firefox every morning by a script run by cron.
Killing the process is ok, but how can I restart it?

The script:
```
#!/bin/bash
kill `pidof firefox-bin`
xhost +127.0.0.1
export DISPLAY="localhost:0.0" && /opt/firefox20/firefox &
exit 0
```

gives the error:
(firefox-bin:9756): Gtk-WARNING **: cannot open display:

Any ideas on how to strat a GUI app from script?

---

### Post by jazzgossen on 2007-02-12
Why do you have the export DISPLAY line there? What happens if you just use "/opt/firefox20/firefox &"? Is the script run from a remote machine, or something?

---

### Post by akosh on 2007-02-12
No, the script is run locally (cron). I was suggested to try "export display" as well: the error is the same when I run it as you wrote.

---

### Post by seppo on 2007-02-12
did you check that the cronjob is run with the user currently having a X-session? My guess is you're running the cron with a different user that is logged in.

---

### Post by g3k0 on 2007-02-12
Are you attempting to use this as root?

---

### Post by koenn on 2007-02-12
I find no difficulties in starting any GUI app from a script - if it is executed while X is already running.
I agree there might be a problem if the owner of the cron job is not the logged-on user but it shouldn't be hard to work around that.

Om my system, the path to firefox is : /usr/bin/firefox

---

### Post by akosh on 2007-02-13
/opt/firefox20 is ok
I do 'crontab -e' logged in as the user, not root, or another user, that should be allright. I've also tried to run the script manually on console terminal.

The situation is that if I login on a console terminal as let's say user1 (average user), X is started and the user is logged in automatically.
If you say that there might be a problem of this kind, I think I have to examine this "autostart-X - autologin" thing.


Thank you for your replies!

---

### Post by gyterpena on 2007-09-05
have a look at this post it worked for me [http://ubuntuforums.org/showthread.php?t=468279&highlight=cron+firefox]("http://ubuntuforums.org/showthread.php?t=468279&highlight=cron+firefox")

---

