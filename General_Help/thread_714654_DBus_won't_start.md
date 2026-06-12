---
title: "DBus won't start"
date: 2008-03-04
forum: General Help
---

### Post by sugardeath on 2008-03-04
I've done a google as well as a search on here for the problem I am having but all the solutions I have come across so far have not worked at all.  In every instance I noticed that when the person typed "/etc/init.d/dbus start" it gave some sort of error or message.  When I type that, I get the following:
```
satoshi@AndrAIa:~$ /etc/init.d/dbus start
satoshi@AndrAIa:~$ 

```

That is to say, nothing.  

Any ideas?

---

### Post by danwood76 on 2008-03-04
well to start dbus you will need to have root privaliges.
```

sudo /etc/init.d/dbus start

```

But it should tell you permission denied, normally dbus is started automatically when ubuntu boots.
Check your running processes in system monitor for:
```

dbus-daemon

```

regards,
Danny

---

### Post by sugardeath on 2008-03-04
Yes, I realize you need the sudo.  It still does the same thing, nothing.

Both dbus-daemon and dbus-launch are currently running.  Dbus refuses to start and as such causes HAL to fail loading and because of *that* i can't access a good portion of my admin settings.

---

### Post by danwood76 on 2008-03-04
> **sugardeath said:**
> 
Both dbus-daemon and dbus-launch are currently running.  Dbus refuses to start and as such causes HAL to fail loading and because of *that* i can't access a good portion of my admin settings.

So Dbus is already running?
Maybe you have more of an issue with HAL.

What exact problems are you getting?
You may need to install some additional DBUS modules, I think theres a few librarys associated with DBUS and HAL.

---

### Post by chrisccoulson on 2008-03-04
Try:
```
sudo /etc/init.d/hal restart
```

I've seen a few posts on the forums from people with race conditions between HAL and DBUS at startup

---

### Post by sugardeath on 2008-03-04
Shouldn't a dbus start or restart give some messages though?  

```
satoshi@AndrAIa:~$ sudo /etc/init.d/hal restart
 * Restarting Hardware abstraction layer hald                                   


```

It just sits there... and sits there...

```
satoshi@AndrAIa:~$ sudo /etc/init.d/hal start
 * Can't start Hardware abstraction layer - please ensure dbus is running
satoshi@AndrAIa:~$ 

```

Aha, so dbus isn't running!

---

### Post by danwood76 on 2008-03-04
Try killing the dbus processes that are running then try to restart them.
it might be that its not giving you messages because dbus has crashed for some reason.

---

### Post by sugardeath on 2008-03-04
I killed dbus-launch and this shutdown both the terminal window I was using as well as Pidgin.  I then tried doing a "sudo /etc/init.d/dbus start" and, again, nothing happened.  Pidgin and the terminal restart just fine, but the dbus processes are gone for good now.

---

### Post by danwood76 on 2008-03-04
Do they come back up after a restart?

---

### Post by tad1073 on 2008-03-04
try this, I was having the same problem and it worked for me.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#HAL](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#HAL)

---

### Post by sugardeath on 2008-03-04
> **tad1073 said:**
> try this, I was having the same problem and it worked for me.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#HAL](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#HAL)

I found that in my initial search and it didn't help me at all.  The problem here is that dbus just doesn't... work.

[quote=danwood76]Do they come back up after a restart?[/quote]

Yes, they do.

---

### Post by funkelauge on 2008-03-05
I had pretty much the same problem. After a tiresome 3 days of crawling through forums and trying all the tricks with rc.d sequences and stuff I've given up. A new install just took me 2 evenings and I had most of my settings and things working.

From now on I'm keen to make a reliable backup to be prepared if things like this happen again!

---

### Post by sugardeath on 2008-03-05
> **funkelauge said:**
> I had pretty much the same problem. After a tiresome 3 days of crawling through forums and trying all the tricks with rc.d sequences and stuff I've given up. A new install just took me 2 evenings and I had most of my settings and things working.

From now on I'm keen to make a reliable backup to be prepared if things like this happen again!

Blah, this looks like a project for Spring Break, then..  Just gotta tough it through another week and a half of school...

Thanks for the help everyone.

---

