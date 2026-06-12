---
title: "How Do I Turn Off Terminal Service"
date: 2007-09-05
forum: General Help
---

### Post by jdkrobinson@gmail.com on 2007-09-05
Hi

I'm new to edubuntu and so far think it's great. However, as I was familiarising (a fancy word for playing around) with the system, I turned on a service called Terminal Mode or something like that (I don't know exactly because I now can't open the services console to check) and it appears to have changed all of my permissions. I used to be able to do any admin task I wanted, sometimes after entering my password again, but now I get "You do not have permission to do that" type messages, and also my wireless USB key will no longer work and I get a "Could not load the HAL" message when it tries to initialise.

Firstly, where is the best place to read about terminal mode, and secondly, how do I turn it off so I can get my admin permissions back?

Cheers

---

### Post by jdkrobinson@gmail.com on 2007-09-08
Nope, nope, my bad.

It appears I had actually disabled dbus, and the fix was here: [https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59946/comments/32](https://launchpad.net/ubuntu/+source/gnome-system-tools/+bug/59946/comments/32)

As this service is right above the Terminal Multiplexor (I found out what it was ACTUALLY called), it was probably just a slip of the mouse.

Cheers

---

