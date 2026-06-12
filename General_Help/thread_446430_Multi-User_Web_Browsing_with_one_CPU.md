---
title: "Multi-User Web Browsing with one CPU?"
date: 2007-05-16
forum: General Help
---

### Post by quickwitt on 2007-05-16
I am opening a cafe and want to install free Web terminals. Ideally I would like to run 2-4 monitors, keyboards and mice from the minimum number of CPUs. Can this be done through any combination of hardware? I am trying to spend as little $$$ as possible.

Thanks in advance!

---

### Post by aysiu on 2007-05-16
Google ```
ubuntu thin client
```

---

### Post by strixy on 2007-05-16
My suggestion would be to contact local computer shops. Not national chains, but local shops. Depending on where you are you can pick up older computers for $50. Xubuntu will install on almost anything, If they're really old and incapable try Zenwalk Linux. I know there is a shop in my city that sells old 1Ghz-2Ghz (depending on the day) with keyboard, mouse and monitors for $50. No good for networked gaming, but internet and email sure! They have buckets of suitable RAM to bump them for $5.

I don't know of any way to do what you are trying to do.

---

### Post by hartz on 2007-05-17
Thin-clients are a good idea for this application.

A single CPU will be fine most of the time.

A single web-page with a flash animation can sometimes hog the whole CPU and make the system slugish or unresponsive for all the connected users.

Multiple users running heavy Java apps could have the same effect - I'm thinking Google-Docs, shuffling pictures arround on Flikr, etc.  Usually these applications are CPU intensive for a fraction of a second, then stop processing mostly while the person is thinking/reading, then becomes intensive again while the screen needs updating, etc. So really it depends on the application, the number of users working simultaneously, and just how objective/irritable they are.

Then there is also video sites.  One or two small videos playing simultaneously should still perform well enough, but this depends on the actual CPU speed quite a lot.

I would recommend that the Workstations have 512 MB ram as they just need to run the X server.  The applications will be running on the Server, so it should have as much RAM as you can throw at it - Firefox is notoriously memory hungry.

What I am very curious about is Audio.  It multiple users are simultaneously watching a different video streams, just how well does xorg deal with making sure each user receives their own sound!!!!?????  This is something that in theory is properly dealt with if you have all the right components running, but your mileage may vary.

In similar vein, Webcams.  I highly doubt that instant messenger / web chat applications running for multiple users on a single machine know how to connect back to the video server on the user's actual X-server machine.  In fact, I am going to go out on a limb here and guess that v4l and v4l2 are not a properly xorg integrated services (like the audio server is), as they should be (It should integrate into xorg at the same level that a mouse or keyboard does).  Someone please correct me if I'm wrong.

A dual-core machine will probably give you a more responsive experience if multiple users are browsing the web and all having CPU-intensive applications/sites/flash/movies/etc simultaneously, but having enough RAM is the most important consideration for the server.  Going from 2 to 4 cores does not give you the same degree of improvement unless you are almost permanently CPU-bound.  (This is where the "load" value of the uptime or top commands become a good guidance, eg add more CPUs if the rounded value of the load value is OFTEN MORE than the number of CPU cores.)

The other part of the browsing experience of the users is what the display on their screens look like.  I would recommend that you add in a graphics card in each workstation rather than use onboard graphics older than 5 years.  If it is less than 5 years old, then even onboard graphics should do for web browsing and email.

So to summarize:
**Thin Client workstations**: Discrete Graphics and 512 MB RAM
**Server**: As much RAM as possible.  Fast CPU or dual-core if you want to spoil them with snappy performance.

This is however quite subjective - for example what constitutes as acceptable responsiveness depends on what your users are used to.  In this regard I'd say get a server which you can upgrade with a faster CPU or more RAM if it doesn't perform well enough.

---

