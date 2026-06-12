---
title: "cache up to 98.8 GB"
date: 2017-04-22
forum: General Help
---

### Post by geoff20 on 2017-04-22
Having a problem with .cache.
It keeps filling up so that I get a warning that there is no longer any space left on my 120 GB SS Drive.
Have emptied a number of times and the only problem seems to be with Kodi. I need to reinstall skin and update library.
Looking at whats in .cache it appears that unity7.log.1.gz is filling up 15 GB last time I looked.
Running Ubuntu 16.04

---

### Post by TheFu on 2017-04-22
Perhaps if you posted the exact files and locations which are growing, someone will recognize them?
Also, you can use **lsof** to see which program is writing to a file.

I'm running kodi as a client/playback device on a raspberry pi.  Not seeing this issue.
```
$ df
Filesystem      Size  Used Avail Use% Mounted on
/dev/mmcblk0p2   29G  2.6G   25G  10% /
/dev/mmcblk0p1  240M   30M  210M  13% /boot
```
As you can see, Kodi doesn't use much storage all all, provided a few settings for the caching aren't enabled. All my media is on a different system.

Also run Kodi occasionally on the storage machine.  My HOME directory on that machine is using 8.3G. The media library is fairly large, BTW.

I do not run Unity, anywhere, so don't have any idea what it may or may not be doing.

---

### Post by Impavidus on 2017-04-22
I don't use unity either, but I know about general guidelines for log files. All kinds of messages get written to unity7.log. After a specific amount of time (which can be a day, a week or something else), the log file is renamed unity7.log.1 and a new log file is started. Later it is renamed unity7.log.2 etc. and it is compressed to unity7.log.2.gz etc. When it's old, at some point it's deleted.

I suggest you look at unity7.log and (if you wish) some older versions and search for repeating messages. When a log file gets very large, we usually see many repeating messages. My .cache is 450MB, 90% of which is in mozilla.
_______________
(Apologies for any typos; it's 1:25 AM, it's [s]Saturday evening[/s] Sunday night, I've watched a movie and drank some wine and I shouldn't run any root commands now)

---

### Post by geoff20 on 2017-04-23
Thanks for the replies.
Still not sure why I had the problem but installed Gnome Shell and hopefully it has gone away.

---

### Post by vasa1 on 2017-04-24
For what it's worth, here's something related that seems to implicate Kodi: [https://askubuntu.com/questions/887220/cache-upstart-unity7-log-growing-to-consume-the-entire-free-disk-space-python](https://askubuntu.com/questions/887220/cache-upstart-unity7-log-growing-to-consume-the-entire-free-disk-space-python)

---

### Post by TheFu on 2017-04-24
On my 14.04 kodi machine, I don't have a ~/.cache/upstart/ directory so there aren't any log files inside there.

Certain machines are too important to run bleeding edge stuff on, like 16.04. The [WAF requirement]("https://en.wikipedia.org/wiki/Wife_acceptance_factor") is higher than any online financial system I can name for stock traders in NYC.  She-who-must-be-obeyed demands it, no exceptions.

I suspect if you don't purge Unity, it will still grow.

---

### Post by geoff20 on 2017-04-25
Interesting reading.
Have not checked the cache on my NUC since changing to Gnome. Better do it soon.
Thanks

---

### Post by geoff20 on 2017-04-25
No problem with cache/upstart since changing to gnome.
Not sure I particularly like the new interface.
Having problems getting the fonts and window headers the correct size for my TV screen.
Will do a search to see if there is a fix.

---

### Post by vasa1 on 2017-04-25
> **geoff20 said:**
> No problem with cache/upstart since changing to gnome.
...
Then kindly mark this thread [SOLVED]: [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

