---
title: "Tell me about remotely administering Ubuntu !"
date: 2007-03-03
forum: General Help
---

### Post by elmerfud on 2007-03-03
I have a friend that wants to get away from Windows.  I am very happy with my Kubuntu installation.  She wants to try it.  She lives hundreds of miles away.  We just cut a Live CD.  

I'd like to be able to help here with things if she gets stuck.  I see that Ubuntu supports remote admin.  Is there a way that I can work on her machine and she can watch as I do it ?  Is there a way that we could chat or talk while I'm doing it ?

Thanks

---

### Post by kidders on 2007-03-03
Hi there,

The most straightforward way to work on a remote machine is via SSH imo, since it's secure, and requires no setup. If you want to chat while you work, perhaps Skype, Jabber, etc. would be useful.

If you want to let your friend see what you're doing on a terminal, I would suggest using **mkfifo** to make a named pipe.

---

### Post by elmerfud on 2007-03-03
That works for me.  I use ssh all the time.  I've never used a named pipe though.  Tell me more about that.   I want her to be able to see what I do so she learns.

---

### Post by Gerard Barberi on 2007-03-03
If you want her to watch as you do it, then VNC.  You just have to have her enable it on her end and port forward any routers.

Not saying VNC is better; i ssh all the time.  In fact I'm doing it right now from work.  Downloading some torrent files.

---

### Post by kidders on 2007-03-03
Sorry... that remark was a bit cryptic! I was referring to a trick you can use to let people in on any CLI magic you might do, so they can follow along in real time...

If you do something like **mkfifo /tmp/watch_this; script -f /tmp/watch_this**, another user can do **cat /tmp/watch_this** to watch you.

Of course, if you decide to type **kdesu konqueror** or something, to take a walk around the remote filesystem graphically, whoever's watching you would probably drown in debug messages!

---

### Post by kidders on 2007-03-03
> **Gerard Barberi said:**
> If you want her to watch as you do it, then VNC.  You just have to have her enable it on her end and port forward any routers.

Not saying VNC is better; i ssh all the time.  In fact I'm doing it right now from work.  Downloading some torrent files.

VNC is certainly a prettier option. :-)

---

### Post by elmerfud on 2007-03-03
I didn't think VNC "echod" the screenshots on the remote machine.  If it does, I'll use it, at least for the stuff I want to show here. 

In Kubuntu, I see XDCMP and remote login as one of the options.  What is that about ? (I'm too lazy to Google at the moment...)

I see VNC4 server/viewer in the repositories.

---

