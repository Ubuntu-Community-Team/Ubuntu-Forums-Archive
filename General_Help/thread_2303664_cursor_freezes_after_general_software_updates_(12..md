---
title: "cursor freezes after general software updates (12.04)"
date: 2015-11-20
forum: General Help
---

### Post by floko2 on 2015-11-20
On my parents laptop, I've recently started all available software updates in Ubuntu 12.04's software center.
(I couldn't wait until everything was downloaded, so I'm not sure if they ended all processes correctly :-/)
However, since then the cursor freezes directly after booting to desktop.

Keyboard is working, I can access console and could type in commands (if only I knew what to type in).

Do you have any idea where to look for the problem?
Thanks a lot for any hints!

---

### Post by raketax on 2015-11-21
Well the contents of /var/log/dmesg could provide an idea, you could try that, if you cannot make sense of it, you can share it here in some sensible form (preferably not just dump it here as post text :D), then someone, maybe me will probably will be able to help you. Also, maybe your system specifications might help, if its a known problem of some piece of the hardware.

---

### Post by floko2 on 2015-11-22
Thanks for pushing me into the right direction!
Took me some time to figure out how to save the file via command line; it's zipped and attached to this post now.
No idea what the log messages refer to... Hope this makes sense to someone.

The old laptop is a Dell Inspiron 1300
running
Ubuntu 12.04.3 LTS Release i386

In worst case I'll simply install Ubuntu anew.
If it's all messy and too complicated to fix things, that might be the cleanest and easiest solution.

Thanks again!

---

### Post by raketax on 2015-11-22
Well, I don't see anything outstandingly wrong with it. However, if you have access to a terminal, and you suspect a failed update process, you can just check by running an update from there using sudo apt-get update && sudo apt-get upgrade
It will need a password. If that fails at any point, then it could be part of the problem.

---

### Post by floko2 on 2015-11-23
Thanks a lot for checking! 
Using sudo apt-get update, I receive a number of errors. 
They are not in English, so I hope my translation matches the standard English error warnings...:

Couldn't get lock /var/lib/apt/lists/lock - open (11: the resource is currently not available)
Unable to lock folder /var/lib/apt/lists/ 
Couldn't get lock /var/lib/dpkg/lock - open (11: the resource is currently not available)
Not possible to lock administration folders (/var/lib/dpkg/), is being used by another process?

Not sure if that helps :-/

---

### Post by raketax on 2015-11-26
It shows that the update process failed in the past, that attempt still holds key files "locked" (prevents others from using them to ensure the safety of the process). Does it show the same after reboot?

---

### Post by floko2 on 2015-11-27
Makes sense... Yes, I rebooted several times since.
Thanks a lot for all your hints so far! However I tried installing a new Ubuntu-Version (14.*) so I could return a working laptop to my parents - and it worked just fine.
Thanks again!

---

