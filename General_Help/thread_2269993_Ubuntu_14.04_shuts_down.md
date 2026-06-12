---
title: "Ubuntu 14.04 shuts down"
date: 2015-03-19
forum: General Help
---

### Post by mark allyn on 2015-03-19
Hello everyone,

About a week ago my ubuntu 14.04 began behaving badly.  If left alone for a few minutes it would "almost" shut down.  By "almost" I mean that if I hit a couple of keys on the console I could hear the hard drive wake up, but nothing would show up on the screen.  The only way I could bring up a new screen was to do a cold boot, at which time I would get a window notifying me that a system problem had occurred and asking if I would like to report it.  

Checking /var/log/syslog I find the following:

[HTML]Mar 19 11:26:20 mark-HP-Compaq-dc5800-Microtower NetworkManager[823]: <warn> error requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.27': no such name[/HTML]


This seems to be associated with the shut-down, or rather, I supppose, the failed start-up.

This is new behavior.  I've had 14.04 installed for a number of months and not had the problem.

Any advice would be most welcome.

Mark Allyn

---

### Post by dino99 on 2015-03-19
that is kind of error after a bad shutdown; nothing scary there.

can you set the 'hibernation' off to see if it helps ?  How is the powersaving set into the bios ? Maybe also an issue with background used (select an other)
are fans working normally ?

---

### Post by mark allyn on 2015-03-19
Hi 9d9-

Thanks for reply.  I have now set "hibernation" off (I'm assuming 'hibernation' is same as suspension--correct me please if I've misunderstood).  We'll see.  The fan sounds fine to me.  I've not played with the background, but will try that as well.  Could you clarify what you mean by " powersaving set into the bios?" 

Mark

9d9-

OK, so I changed the background and set suspend to "indefinite" or "never" and they didn't do the job.  Overnight it put itself to sleep and couldn't be roused from the keyboard.  Cold boot was required.

Any further ideas?

Mark

---

### Post by dino99 on 2015-03-20
if it's an old config (i mean multiple successive dist-upgrade vs fresh install) then maybe your 'profile' is borked. You can create a new user to check if it also happen; or simply rename your profile (with a suffix or else) then reboot, the system will recreate a new profile with your actual user login.

---

### Post by tiger2000 on 2015-05-28
I got the same here. It seems that some "software update" or "core update" mess up something. 
The weird error is : if Ubuntu goes suspend, when it goes back, it asks my user and login again in a cold boot. It's very weird. 
It had worked fine for months !

---

