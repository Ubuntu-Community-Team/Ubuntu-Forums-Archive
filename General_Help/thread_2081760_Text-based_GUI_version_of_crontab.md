---
title: "Text-based GUI version of crontab"
date: 2012-11-07
forum: General Help
---

### Post by cazz on 2012-11-07
Hi, I wonder if someone know a good script or something that make it easy to add, edit or remove schedule.

I like to easy change a schedule from SSH but I don't know what is the easy way to do that.

---

### Post by CaptainLinux on 2012-11-07
Your best bet is probably to generate the syntax using an online service.

[http://www.corntab.com/](http://www.corntab.com/)

---

### Post by cazz on 2012-11-08
ahh thanks :)

---

### Post by Habitual on 2012-11-08
There's kcron for KDE users but that's about it.

---

### Post by cazz on 2012-11-08
I wonder if that is any web GUI för crontab that is easy to use.

---

### Post by HermanAB on 2012-11-08
export EDITOR=gedit
crontab -e

---

### Post by Habitual on 2012-11-08
> **cazz said:**
> I wonder if that is any web GUI för crontab that is easy to use.

Since you asked. ;)
[http://www.robertplank.com/cron/](http://www.robertplank.com/cron/)

---

### Post by cazz on 2012-11-09
ohh thanks, they both are very nice.

But I mean if I add a webserver on my linux, is that any basic but good crontab to management from the web?

---

### Post by Habitual on 2012-11-09
> **cazz said:**
> ohh thanks, they both are very nice.

But I mean if I add a webserver on my linux, is that any basic but good crontab to management from the web?

Oh, a web interface for your own host/system?
Webmin can do that easily, but that seems  like overkill just for a cron editor, no?
But [it has lots of other features]("http://byethost.com/vpsplans/webminfeatures") too, not just cron interface.

---

