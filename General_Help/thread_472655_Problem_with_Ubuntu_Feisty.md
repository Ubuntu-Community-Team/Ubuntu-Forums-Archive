---
title: "Problem with Ubuntu Feisty"
date: 2007-06-13
forum: General Help
---

### Post by amdfanboy on 2007-06-13
here's the situation...

I installed vmware in my ubuntu feisty fawn...then after doing so, i created a virtual machine, namely Windows XP Home Edition..

Vmware opted to allocate a space for that virtual machine, due to the fact that it is chosen by default, I clicked OK to go with the default configurations...

Still haven't managed to boot that virtual machine, I then restarted my pc...

In the login screen, I tried to log-in as root, but it says

"System administrator doesn't allow this user to log in at this screen" (or something like that)

In doing so, I proceeded with my default user, namely "amdfanboy"

Then a notice appeared that, ubuntu can't start because the hard drive is full....what the heck...did vmware do this on purpose? are the default values of vmware configs are that tricky?

I just went on with the default configs then suddenly it said that the hard drive is full?

and if possible, how can I log-in as root besides from the terminal...I tried logging-in via switch user, nothing happened...same screenie appears...

---

### Post by badactress on 2007-06-13
I've never used VMWare so could be completely wrong but.. 

Most virtual machines create a virtual hard-drive in the form of a huge file for your virtual machine to use.. If this is what is chocking your drive, then logging into the terminal, tracking this file down & deleting it should free enough space to allow Ubuntu to startup.

You could possibly look for a hidden folder in your home folder called .vmware or similar.. Might be in there? 

Sorry for being vague! I just noticed nobody else had replied yet!

:)

---

### Post by amdfanboy on 2007-06-13
ok i'll try that one out

---

### Post by timcredible on 2007-06-13
vmware puts everything into one file.  that file doesn't grow, it starts out at whatever size you specify at the beginning, so if you specified 8gb, that's how big the file is.  if need be, just boot with the livecd, delete that file, then boot normally.  in fact, i wouldn't try booting the system off the hd if it's full (i'm assuming here that you put the /home directory and the root directory / in the same partition).

---

