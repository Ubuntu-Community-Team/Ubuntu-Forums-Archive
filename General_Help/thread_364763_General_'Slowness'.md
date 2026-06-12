---
title: "General 'Slowness'"
date: 2007-02-18
forum: General Help
---

### Post by tpdasf on 2007-02-18
Since using Ubuntu I've been experiencing a general slowness of everything. I keep reading that for the same hardware Linux should be faster, but with Windows XP, opening up a folder was instantaneous, same with a web browser and all programs. In Ubuntu, a file browser takes about 3 seconds, firefox can take around 10 seconds sometimes.
I'm running Ubuntu Edgy and Gnome, but it has always been like this.

Any suggestions?

Thanks

---

### Post by Maestro23 on 2007-02-18
What are your system specs?

---

### Post by tpdasf on 2007-02-18
512mb DDR RAM, about 60gb of hard drive space on this partition, AMD XP 2000+

---

### Post by Turmoyl on 2007-02-18
Make sure you have the 2 entries for your localhost in /etc/hosts:

127.0.0.1 localhost
127.0.1.1 <hostname>

---

### Post by tpdasf on 2007-02-18
Yes, they're both there

---

### Post by russell.h on 2007-02-18
Check the system monitor and see how much RAM you're using.

Also, if you log in, open firefox, close it, (you can wait a minute if you want), then open it again, does it open faster the second time?

And how long ago did you install windows? Windows is pretty snappy when you first install it, but after a year or so it is just unbearable, especially if you install a lot of SDKs, specialized drivers, etc (even if you uninstall them the computer won't get any faster). 

Linux doesn't have that problem, having more programs running in the background will certainly slow things down, but if they aren't running, or as soon as you uninstall them they quit affecting your system's speed.

---

### Post by tpdasf on 2007-02-18
System Monitor shows around 50-60% of User memory being used while idle. (The only things I have open are amarok, GAIM, Firefox)

Yes, firefox is faster the second time.

I installed Windows about 3 years ago, I try to keep it clean and it still runs fine. (Windows XP)

---

### Post by llamakc on 2007-02-18
Have you setup hdparm?

---

### Post by tpdasf on 2007-02-18
Sorry, not sure what that is

---

### Post by RyanOmailley on 2007-02-18
I, too, am experience general sluggishness when compared to XP. Especially when resizing windows.

---

### Post by tpdasf on 2007-02-19
Anyone?

---

### Post by r4ik on 2007-02-19
-

---

### Post by kerry_s on 2007-02-19
You should try Xubuntu. Gnome is made to be simple not fast, xfce4 is built to run fast even on lower spec systems. But you can also just use alternative apps that work much faster. Even in xubuntu i've switched the apps around and use faster apps instead of pretty detail laden apps, it ain't pretty but its fast. :)

---

### Post by tpdasf on 2007-02-20
I'm too used to the little details in Gnome now to switch :P, although I might give xubuntu a try.

r4ik, are you sure you're replying to the right thread?

---

### Post by Boomy on 2007-02-20
Showing folder contents with Linux (and OSX) has always been slower than XP in my experience. I'm not sure why. I think Windows has the folder view stored some kind of cache and Linux and Unix refresh the contents every time  you view it? :confused:

---

### Post by r4ik on 2007-02-20
> **tpdasf said:**
> I'm too used to the little details in Gnome now to switch :P, although I might give xubuntu a try.

r4ik, are you sure you're replying to the right thread?

Oops Thanks.

---

### Post by Darko Beta on 2007-02-21
Not sure if this applies to you, but I had the same problem and it was because I had an ATI 9550 card.  When I would switch to the desktop it would have to draw the icons--firefox was slow--everything was slow.  I finally switched to an Nvidia 6600GT, admittedly with better specs, but now my Ubuntu flies.  Everything is much snappier, and I can even run Beryl with no problems.  I have a P4 1.8ghz with 1gb ram, for reference.  I wasn't crazy about buying a new card, but I am happy to support Nvidia who is at least providing some decent drivers.

---

