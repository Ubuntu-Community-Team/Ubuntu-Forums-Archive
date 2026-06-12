---
title: "cron job not working"
date: 2006-11-29
forum: General Help
---

### Post by compudude86 on 2006-11-29
im having problems with the cron job not working. here is my entry

```

root@WEB:/etc# crontab -l
* * * * * /open2300-1.10/ham2300
```

but if i run it on its own, it does work. i also did the "echo to test.log" test, which functioned.

---

### Post by scxtt on 2006-11-29
what are the contents of ham2300, i take it that's a script?  could be a $PATH problem for root ... also, at least in /etc/crontab there's 6 fields before you enter the command, the one you're missing would be username, before the command ...

also, i don't think "* * * * *" would be a valid time designation -- that would be "start all the time" ...

---

### Post by compudude86 on 2006-11-29
no, its an executable. its a weather station data sender, that i need set to send once every minute.

---

### Post by scxtt on 2006-11-29
then something like:

0-59 * * * * /open2300-1.10/ham2300

would work better ... what version/type of cron are you using?

---

### Post by compudude86 on 2006-11-29
version 2.3, apt-get says its up to date.

---

### Post by compudude86 on 2006-11-30
there is also a copy of the program in /usr/local/bin, here is my path from the crontabs folder if it helps:
```
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

``` if that helps

---

### Post by compudude86 on 2006-11-30
ok, so if i run ham2300 from anywhere else in the system, it runs properly. but if i try typing the ham2300 command from inside the /var/spool/cron/crontabs directory, it doesnt return a command not found, but it doesnt run.

---

### Post by scxtt on 2006-11-30
try putting:

0-59 * * * * root /open2300-1.10/ham2300

in /etc/crontab

and you're positive the program is run from
/ --> open2300-1.10 --> ham2300 ... ?  so you're using the full path in your cron entry, paying attn to the format of the other entries in that file ...

---

