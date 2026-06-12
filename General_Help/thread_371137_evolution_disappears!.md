---
title: "evolution disappears!"
date: 2007-02-26
forum: General Help
---

### Post by secretspicy15 on 2007-02-26
I have been running Evolution since installing Ubuntu a few weeks ago and have had no problems. It happily fetched mail from my pop3 university email account as well as synching with my exchange account for work. This morning it started freaking out asking me for my password for exchange repeatedly.  I got out of it and restarted evolution. When I opened evolution again,it showed on my panel [Starting Evolution Mail...] and then it disappeared, without ever showing the GUI. I tried opening evolution again, and the same thing happened. I then looked at my system monitor and two copies of evolution were running at once. I killed them and their processes, and tried again. Same thing. I ended that instance and its processes, and restarted the computer. same thing happens once more. AHHH I'm going crazy, I hate the web interface for my email. Perhaps I'll just get thunderbird.  But If anyone has any ideas please let me know! :-) thanks
-TJ

---

### Post by bapoumba on 2007-02-26
Do you have any error if you launch evolution from a terminal (> Accessories > Terminal> and run **evolution**) ?

---

### Post by secretspicy15 on 2007-02-26
When I run it from the terminal it just says
```
CalDAV Eplugin starting up ...
```
and hangs indefinitely. (or until I cntrl-C it)

---

### Post by bapoumba on 2007-02-26
[https://launchpad.net/ubuntu/+source/evolution/+bug/57555]("https://launchpad.net/ubuntu/+source/evolution/+bug/57555")
There is a closed bug about that, that looks fixed in edgy. Is your system up to date ?
```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by secretspicy15 on 2007-02-26
Thanks for your help! I can't try it right now, I have to use windows (boo) for a class project, but will try as soon as i'm done and can return to ubuntu. :biggrin: 
-TJ

---

### Post by secretspicy15 on 2007-02-27
Well, I tried updating and upgrading, but all it did was upgrade firefox -- evolution still disappears / freezes on the CalDAV plugin step... Oh well, I've been using thunderbird since then and it works fine(better even, it seems faster). I'd just like to have the exchange support that evolution had.
Thanks for your help anyway!
TJ

---

