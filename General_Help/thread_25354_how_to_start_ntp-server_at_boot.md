---
title: "how to start ntp-server at boot"
date: 2005-04-09
forum: General Help
---

### Post by rosslaird on 2005-04-09
OK, I've looked at a few threads (and I've searched), but as usual I can't quite figure this out. I want to start the ntp-server at boot time. I think the method involves this:

update-rc.d ntp-server start

but then what? I think I need to add the runlevel (3?) to the command. And is my syntax right? I did look at the update-rc.d man page, but I can hardly ever make sense of those man pages...

Help would be appreciated.

Thanks.
Ross

_____
Update:

After more searching, I tried this:

sudo update-rc.d ntp-server defaults

but I got:

System startup links for /etc/init.d/ntp-server already exist.

But ntp-server does not start at boot. I have to do this after boot:

sudo /etc/init.d/ntp-server start

Hmm.

---

### Post by heimo on 2005-04-10
```
sudo update-rc.d  -f ntp-server remove
sudo update-rc.d ntp-server defaults

```

This should first remove start/stop links and then create default links to start ntp-server on levels 2,3,4,5 and stop on levels 0,1,6, which is what you most probably want to do.

---

### Post by rosslaird on 2005-04-10
Yup, that worked.
Thanks very much.

Ross

---

### Post by jonrkc on 2005-05-22
[QUOTE=rosslaird]Yup, that worked.
Thanks very much.

Ross[/QUOTE]
 Thanks from me, too.  I couldn't get ntp-server inserted to start at boot using Ubuntu boot manager (ubm), but your little script seems to have done the trick, and now it shows up in the list of services for the first time.

I'll keep an eye on my clock and see if ntp-server is doing its job.  I couldn't find a configuration script equivalent to some other distros' scripts for ntpd anywhere.

EDIT: I found the configuration script, /etc/ntp.conf, and discovered that the line to enable talking to the world-wide ntp pool was still commented out.  Uncommenting it finally seems to have got ntp-server communicating with a time-server.  

Don't know why this couldn't be automatic at installation-time, but anyway I guess it's OK now.

---

