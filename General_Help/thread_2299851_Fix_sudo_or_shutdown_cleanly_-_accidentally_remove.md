---
title: "Fix sudo or shutdown cleanly - accidentally removed user from sudo group"
date: 2015-10-21
forum: General Help
---

### Post by atconc on 2015-10-21
I messed up and when trying to add my one sudo user to a new group used the command usermod -g (without -a) so my user is now only in the new group and therefore no longer in the sudo group.

The machine is headless, running ubuntu server 14.01 and usually managed by ssh, it's in a space where it will be difficult to connect a keyboard and monitor without first powering it down (I usually ssh in and shut it down and then move it if I need to connect to a monitor).

I don't want to hard power down as I have a MDADM RAID 5 that I would worry about corrupting. 

So ideally is there anything I can do over ssh to restore root or cleanly shutdown?
If not is there away to cleanly shutdown if I take a monitor and keyboard to the box?
Or any other suggestions?

It is connected to a UPS and running APCUPSD so I was also thinking of trying disconnecting the power from the UPS and hoping that the ups software still works ok and shuts down cleanly.

Any suggestions gratefully received!

---

### Post by TheFu on 2015-10-22
If the open file systems are not too active, the journaling features should handle it well-enough.
Shutdown any DBMS, type "sync<enter>" 3 times, then pull the plug.  It is important to type it. Don't copy/paste. It is a timing thing.

As you've already guessed. Short of hacking in with an escalation to root crack, I don't think there is any way to fix this besides booting off a live-boot, mounting the partition where /etc/ is and manually fixing the group file.  BTW,  I've hardly ever use the addgrp/grpadd command-editing the group file directly is much easier on systems that don't use ldap/remote authentication. Just sayin'.

---

### Post by atconc on 2015-10-31
Thanks for replying - sorry it's taken so long to update.

In the end I pulled the power from the UPS and when the battery got low it forced a clean shutdown.  I then was able to fix everything from a recovery console.  Less learnt as far as managing groups goes! I've added a password to the root user too as another fall back option if I mess this up again....

---

