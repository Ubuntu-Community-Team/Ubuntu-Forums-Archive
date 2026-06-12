---
title: "Software center no workie after upgrade to 14.04"
date: 2014-04-25
forum: General Help
---

### Post by borischan on 2014-04-25
For a few days software center refuses to open, seems it tries to start, window turns gray then crashes. I sometimes get a message reporting failure, like that's necessary ;)
Any ideas how I can troubleshoot this problem?

Edit:
From terminal I get this:-

mi**@****ubuntu:~$ software-center
2014-04-26 08:11:54,654 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-04-26 08:11:56,286 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2014-04-26 08:11:56,288 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2014-04-26 08:11:56,293 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2014-04-26 08:11:56,293 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2014-04-26 08:11:56,400 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
No bp log location saved, using default.
[000:000] Cpu: 6.23.6, x2, 2667Mhz, 2015MB
[000:000] Computer model: Not available
[000:000] Browser XEmbed support present: 1
[000:000] Browser toolkit is Gtk2.
[000:015] Using Gtk2 toolkit
[000:074] Warning(optionsfile.cc:47): Load: Could not open file, err=2
[000:074] No bp log location saved, using default.
[000:075] Cpu: 6.23.6, x2, 2667Mhz, 2015MB
[000:075] Computer model: Not available
[000:075] Browser XEmbed support present: 1
[000:075] Browser toolkit is Gtk2.
[000:075] Using Gtk2 toolkit
No bp log location saved, using default.
[000:000] Cpu: 6.23.6, x2, 2667Mhz, 2015MB
[000:000] Computer model: Not available
java version "1.7.0_51"
OpenJDK Runtime Environment (IcedTea 2.4.6) (7u51-2.4.6-1ubuntu4)
OpenJDK Server VM (build 24.51-b03, mixed mode)
Bus error (core dumped)


Tries to open, then the same crash

---

### Post by matt_fussell2 on 2014-04-25
Have you tried removing and reinstalling software center from the command line? If you're brave enough to to do it, you could purge it and then re-install:
```
sudo apt-get purge software-center && sudo apt-get autoremove && sudo apt-get clean && sudo apt-get install software-center
```

---

### Post by borischan on 2014-04-25
Thanks for the reply, tried that but still the same

---

### Post by trag on 2014-04-26
I have given up on the ubuntu software center(its a hopeless pile of dung)  and switched to the Deepin software center.Get the Deb. file here  [http://www.omgubuntu.co.uk/2012/01/how-to-easily-install-the-slickest-software-center-on-linux](http://www.omgubuntu.co.uk/2012/01/how-to-easily-install-the-slickest-software-center-on-linux).
good luck
trag

---

### Post by matt_fussell2 on 2014-04-27
You might also give Synaptic:
```
sudo apt-get install synaptic
```

---

### Post by borischan on 2014-04-28
Gave up, complete fresh install was necessary. Actually "upgrade" to 14.04 was full of fail so I started from scratch.

---

### Post by mörgæs on 2014-04-28
Good, please mark the thread 'solved'.

---

### Post by borischan on 2014-04-28
> **mörgæs said:**
> Good, please mark the thread 'solved'.

I could do, but nothing was solved, was it? Look at the title, "no workie after upgrade to 14.04"
If the solution to issues caused by upgrading is always a fresh install, then please add that comment at the top of the forum.
How about, "Upgrades suck, start again"

You are really a mod?

---

### Post by mörgæs on 2014-04-28
I am. Kid you not.

1) "Solved" would indicate to people who are trying to help that they don't have to open the thread and read through it all, wasting their time.

2) I know that you don't but some people with a similar problem might consider a reinstall an acceptable solution.

---

### Post by borischan on 2014-04-29
> **mörgæs said:**
> I am. Kid you not.

1) "Solved" would indicate to people who are trying to help that they don't have to open the thread and read through it all, wasting their time.

2) I know that you don't but some people with a similar problem might consider a reinstall an acceptable solution.

1) Weird that, solved to me indicates that inside a thread, there maybe a solution that I am looking for, hence the word "solved". If the solution is that Ubuntu upgrade is crap, install Windows or some other OS, would you consider that a suitable resolution?

2) Correct, a re-install is not an acceptable solution to an unacceptable problem. There were other issues too, no point highlighting them here.
"  Fast, free and incredibly easy to use, the Ubuntu operating system powers millions of desktop PCs, laptops and servers around the world."

Fast maybe, free certainly, incredibly easy to use until "it" hits the fan. Then mods on the Ubuntu forum act like asses, not the first time for your information, even in my limited posting experience.

So, not solved, shall we say, put off for a while... till the next time...

---

### Post by mörgæs on 2014-04-29
Good for you that you are able to put problems off, but something tells me that you are able to put people off, too. 


Seems like the thread has run its course. Closed.

---

