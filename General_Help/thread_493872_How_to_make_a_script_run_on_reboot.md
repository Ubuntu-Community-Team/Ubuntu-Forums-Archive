---
title: "How to make a script run on reboot?"
date: 2007-07-06
forum: General Help
---

### Post by william_hunter on 2007-07-06
OK, I have  a shell script I use to boot another program, and I want to make sure that shell script is loaded every time the server restarts automatically. How can I go about doing this?

---

### Post by reckless2k2 on 2007-07-06
i think this is what you're asking:

[http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by william_hunter on 2007-07-06
Heh...yes, it looks about right. Thanks.

---

### Post by Spudgun on 2007-07-06
Alternatively, you could create a [cronjob]("http://www.hmug.org/man/5/crontab.php") to do it.

---

### Post by william_hunter on 2007-07-06
Actually, that looks promising. Can I set a cronjob up to run a shell script named nwnstartup.sh  3 minutes after startup or something along those lines? I want to give the system time to get booted and stable, and to allow firestarter to fire up and get the ports forwarded.

---

### Post by mannheim on 2007-07-06
I think you can combine "cron" and "at" to do this. The program "at" can run an exutable script named "foo.sh" three minutes from "now" using the syntax
```
echo "/path/to/foo.sh" | at now + 3 min 
```
So you can add a crontab line to /etc/crontab, or to a file in /etc/cron.d, containing something like
```
@reboot root echo "/path/to/foo.sh" | /usr/bin/at now + 3 min
```

---

