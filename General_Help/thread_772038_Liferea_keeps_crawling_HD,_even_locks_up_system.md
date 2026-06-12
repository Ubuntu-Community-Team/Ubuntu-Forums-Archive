---
title: "Liferea keeps crawling HD, even locks up system"
date: 2008-04-28
forum: General Help
---

### Post by matthias_k on 2008-04-28
In Hardy I observe strange behavior related to Liferea:

When starting it for the first time (after each reboot that is), it will take exceptionally long for the application to completely load (maybe 20 seconds). After loading up, Liferea will keep accessing my hard disk for minutes, as if it would be crawling something.

During that period the system seems to be very unstable: It becomes laggy and I even experienced a system hard lock when following a link in a Liferea feed. I mean, the system really locked up completely, I could not even ALT+CTRL+x out of X11, had to pull the plug. This has never happened before with any Ubuntu I used (and I used them all except Wharty). But then again, maybe the crash was just coincidental (but not less critical -- especially for an LTS release!)

I am not 100% sure if it's really Liferea causing the trouble (mainly because "top" doesn't indicate Liferea getting much CPU resources), but there is some strong indication (like the HD LED turning off after exiting out of Liferea). First I suspected Tracker or updatedb to be the troublemaker, but during these HD accesses the Tracker icon said "Idle" and "top" didn't indicate any CPU resources being allocated to Tracker or updatedb.

Do anyone of you have similar issues?

---

### Post by goodmanbrown on 2008-11-02
I had slow startup times and tons of harddisk spinning with liferea.  It turned out that the sqlite database behind liferea was badly fragmented.  If you've been running it a long time, you might have the same problem.

Following the instructions at:

[http://liferea.blogspot.com/2008/08/how-to-run-vacuum.html](http://liferea.blogspot.com/2008/08/how-to-run-vacuum.html)

fixed the problem for me.  In short:

1. Shutdown Liferea
2. Start the sqlite client by running: "sqlite3 ~/.liferea_1.4/liferea.db"
3. At the prompt enter: "VACUUM;"
4. Wait until the prompt reappears.
5. Restart Liferea

(To quit out of sqlite, enter: ".q")

---

