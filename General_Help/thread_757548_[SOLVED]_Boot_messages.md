---
title: "[SOLVED] Boot messages"
date: 2008-04-17
forum: General Help
---

### Post by bilijoe on 2008-04-17
Sometimes, when something unusual happens during boot up--e.g., when the system decides a filesystem needs to be checked--all the commands issued during boot up, along with the response line(s) they return, are visible on the screen.  When this happens, I often see things that look like they may require attention, like the fact that the system couldn't start firestarter, and some things that scroll by so fast, all I can catch is the bright red "[FAILED]" tag, at the right edge of the screen.  Is there a way to cause these messages to appear (as opposed to waiting for the next time the system wants to do some maintenance, and decides to post them so I'll know what's taking so long)?  And is there a way to "pause" the boot process so the messages can be read?  Or better yet, to redirect them into a text file, so they can easily be viewed in their entirety?  I have looked in all the logs I can find, including what sounded (by its name) like it might be such a log, but it simply said "Nothing has been posted yet."  These days, I'm reborn as a rank newbie, but in a past life I was a hard-core "old school" Unix user (administrator), and I remember, every time I had to boot a system (which was rare--we just let them run for months, even years, at a time), several of us would gather (in hopes of catching everything of importance) and scrutinize the boot-up messages, as they flew by.  We considered it an important component of restarting a system.  I'm used to just trusting the system, for the most part, these days, but I would like the ability to "watch" the system boot, once in a while.  Right now, I'd kind of like to see what the deal is with firestarter not starting.  In any case (I know I'm getting long-winded here--sorry), if anyone knows a way to force the boot messages to be displayed, or (better) a way to capture them in some kind of a log file, I'd truly appreciate hearing about it.  Being able to ask for information, in this way, is so great, it alone would make it worth switching from Windows to Linux.  I don't know which is the real bonus--these forums, or the fact that Linux is such a superior operating system.  But I don't have to know or care--switch to Linux, and you get both.  Go with Windows, and you get... well, Bill Gates, for one (enough said?).

---

### Post by sekinto on 2008-04-17
To see what "failed":
```
sudo grep failed /var/log/messages
```
To see everything:
```
sudo cat /var/log/messages
```

---

### Post by kutjara on 2008-04-17
If you want to see the boot messages every time you boot your machine, you can edit your menu.lst file to use verbose mode, which will show you everything that's happening.

To do this, type:

```
sudo gedit /boot/grub/menu.lst
```

Look for the entry representing your kernel and delete the words "quiet" and "splash". Then save the file. This will remove the Ubuntu splash screen and give you a scrolling display of the boot process.

---

### Post by bilijoe on 2008-04-17
sekinto wrote:
> **sekinto said:**
> To see what "failed":
```
sudo grep failed /var/log/messages
```To see everything:
```
sudo cat /var/log/messages
```

I tried this, and, quite obviously, everything is in that file, but it is in a very different form--far less human friendly--from what I see when the messages print to the screen.  For example, I found no references to firestarter, at all, and I know there is at least one command line that scrolls by that launches (or attempts to launch) firestarter.  The last time I saw these messages, there were several attempts made, at different points in the boot process, to start firestarter.  The messages in this file are far too cryptic for my purposes.:confused:  I just want to see (and, preferably capture, for easier viewing, and reviewing), the commands, as they are issued, from the various script files that run at boot up, and the command line output they produce.  Plain old English stuff.

---

