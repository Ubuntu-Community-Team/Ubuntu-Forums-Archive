---
title: "Kubuntu doesn't load into Desktop environment"
date: 2007-12-29
forum: General Help
---

### Post by PookyHello on 2007-12-29
Hi... When going into Kubuntu it doesn't load into the Desktop. It says these things:
kinit: name_to_dev_t...
kinit: trying to resume from /dev/disk/by-uuid...
kinit: no resume image, doing normal boot...

How do I fix this?
Thanks!

---

### Post by PmDematagoda on 2007-12-29
Boot Ubuntu in Recovery Mode and then see if you can get to a terminal properly.

---

### Post by mattinrom on 2007-12-29
my system does that its not the reason ur desktop env is not loading that just means that it was checking if the system was in hibernation mode or not. DO u get a logon propmt?

---

### Post by PookyHello on 2007-12-29
In recovery mode it does the same thing.

---

### Post by jeffus_il on 2007-12-29
What you posted is not a problem, just a check to see if the system was "hibernated" and whether to restore the previous state.

What does your last screen look like, What is the final state your machine reaches after boot??

---

### Post by PookyHello on 2007-12-29
Sorry guys I'm really a noob... It asks me for my login. That's the final stage.

---

### Post by jeffus_il on 2007-12-29
Do you have a username and password that you can enter at the login screen?

---

### Post by davidingram on 2007-12-29
I have the same problem, no GUI anymore.  It used to work fine, then i plugged in an external monitor and used that as a second screen.  After that i'm unable to restart the GUI, i get a similar error message:
 kinit: name_to_dev_t(/dev/disk/by-uuid/...........[a whole bunch of hex numbers...]...
kinit: trying to resume from /dev/disk/by_uuid/.....[the same hex numbers]...
kinit: No resume image, doing normal boot...

then i get to a login prompt.  I can login with my user name and password but then it just lands me at some sort of prompt.

Any ideas, anyone?

---

### Post by davidingram on 2007-12-29
Hey Pookyhello, I just found this and it has fixed it.

[http://ubuntuforums.org/showthread.php?t=649233&highlight=doing+normal+boot](http://ubuntuforums.org/showthread.php?t=649233&highlight=doing+normal+boot)

I still have no "shutdown" option when i try to shutdown (just hibernate, suspend, etc), but I am working on that.  At least I have my GUI back

Maybe this will help you too

D

---

