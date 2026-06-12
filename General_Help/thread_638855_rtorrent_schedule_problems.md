---
title: "rtorrent schedule problems"
date: 2007-12-12
forum: General Help
---

### Post by lavasaurus on 2007-12-12
I've recently started using rTorrent to manage my torrents. The actual application works fine, but I've been trying to configure the .rtorrent.rc which has led me to some problems.

I'm trying to use the schedule command so that a script will be executed every x seconds. Right now I have:

```
schedule = foo,5,5,"execute=~/.torrents/scripts/torrentGrabber"
```

when I open up rTorrent, I get "Scheduled command failed: foo: Variable "execute" does not exist" every 5 seconds. (At least I got the 5 second part right!)

What this all comes down to is...I have no idea how the schedule command (or any of the commands, at that) are supposed to work. I've looked at the man page for rtorrent which provides a *little* help about it, but I'm still missing some large chunks in my understanding.

The first argument is an ID. Is that arbitrary, or is there a list of valid IDs (like move_complete, etc). Also, execute is supposed to be a command, but the error seems to imply that it thinks it is a variable. I don't know why.

Is there any more complete documentation for rtorrent around? I've looked around for answers a good bit, but haven't really run into anything much.

---

### Post by Dmole on 2008-01-08
rtorrent is not a scheduler by breed so you would be better off using the standard linux scheduler ... don't remember the name but google will 

keep in mind that the version of rtorrent you have might not support what your documentation is telling you to do.(try getting something up to date off the svn)

---

### Post by Dmole on 2008-01-08
cron is what you want

---

### Post by HornedBeast on 2008-05-01
I wrote an Rtorrent schedule guide as part of my media server setup.

I think its step 6.

[http://ubuntuforums.org/showthread.php?t=775906&](http://ubuntuforums.org/showthread.php?t=775906&)

The link is above.

Hope that helps.

---

