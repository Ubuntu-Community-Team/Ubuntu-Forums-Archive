---
title: "unexpected errors, what must I do?"
date: 2013-02-18
forum: General Help
---

### Post by dumble on 2013-02-18
I frequently get unexpected errors. Maybe it has something to do with [this]("http://ubuntuforums.org/showthread.php?t=2115746") problem. Here is an example:
[IMG]http://i275.photobucket.com/albums/jj290/dumbl3/FORUM/Screenshotfrom2013-02-18134228_zpsdc507253.png[/IMG]

What must I do?

---

### Post by dino99 on 2013-02-18
might be due to the ram settings on that system (data badly synced) and so ubuntu cant be blamed.

but if you understand system well enough and are able to troubleshoot on the fly, then you can make some tweaks (but at your own risk, as usually said indeed)
[http://unix.stackexchange.com/questions/30286/can-i-configure-my-linux-system-for-more-aggressive-file-system-caching](http://unix.stackexchange.com/questions/30286/can-i-configure-my-linux-system-for-more-aggressive-file-system-caching)

---

### Post by grahammechanical on 2013-02-18
May I suggest that you remove the tick mark against Send an Error Report to Help solve this Problem and the click Continue and carry on working?

Are you able to carry on working? I run the development version of Ubuntu we sometimes get these error messages. Well, it is a version under development. We expect this kind of thing. We have the choice to report it or ignore it.

If you do not have a Launchpad account you will not be able to report it. 

This issue may be resolved in few days time when an update may fix the problem.

[https://wiki.ubuntu.com/Apport]("https://wiki.ubuntu.com/Apport")

Regards.

---

### Post by Yellow Pasque on 2013-02-18
Report it (or at least go through the process to the part where apport searches for duplicate bugs). With a segfault (SIGSEGV), chances are that someone else has experienced the same segfault and it will take you to that bug report, wher you might find further guidance.

If nothing else, a critical error like that should be reported against an already released version (12.10).

---

