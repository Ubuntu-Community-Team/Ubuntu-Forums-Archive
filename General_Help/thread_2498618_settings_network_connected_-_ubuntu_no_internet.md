---
title: "settings network connected - ubuntu no internet"
date: 2024-06-21
forum: General Help
---

### Post by jgw on 2024-06-21
My settings network is connected but my ubuntu has no internet.  Up to now this machine was working just fine (yesterday) but today it is not.  Nothing has changed.  Here are some things I have done:  pasted at: [https://paste.ubuntu.com/p/ghCS5kP5K7/](https://paste.ubuntu.com/p/ghCS5kP5K7/)

This time its not fixing itself

---

### Post by grahammechanical on 2024-06-21
> My settings network is connected

Do you mean that the router/hub/modem is connected to the Internet Service Provider (ISP)? Is the computer connected to the modem by Ethernet cable? When you open System Settings>Network what do you see? Is there a slider that activates and deactivates the Ethernet adapter?

Can you access the BIOS/UEFI settings utility to confirm that Ethernet is still enabled?

Are you dual booting with Windows? Is Ethernet switched in Windows? 

The same checks can be done for WiFi if you are wanting to use that.

We need to eliminate the obvious.

Regards

---

### Post by jgw on 2024-06-21
My settings tell me that my network is connected.  ie. "Connected - 100Mb/s" and the switch is red   The problem is that I think that the network master is not recognizing the connection.  Oh, if also have Wi-Fi but I have turned it off (makes no difference)

Can you access the BIOS/UEFI settings utility to confirm that Ethernet is still enabled?  Do you have a program you want me to run for that?

Are you dual booting with Windows? Is Ethernet switched in Windows?  I do not have Windows on this machine.

I have one posted (system-info) at [https://paste.ubuntu.com/p/nKCPMKjDD2/](https://paste.ubuntu.com/p/nKCPMKjDD2/) and (hardinfo report) [https://paste.ubuntu.com/p/BBDc5z3H6r/](https://paste.ubuntu.com/p/BBDc5z3H6r/)   The first two will tell you stuff about my machine in some detail.

---

### Post by currentshaft on 2024-06-21
> **jgw said:**
> My settings network is connected but my ubuntu has no internet.  Up to now this machine was working just fine (yesterday) but today it is not.  Nothing has changed.  Here are some things I have done:  pasted at: [https://paste.ubuntu.com/p/ghCS5kP5K7/](https://paste.ubuntu.com/p/ghCS5kP5K7/)

This time its not fixing itself

I advise against showing "nmcli con show" output since the list of SSIDs points out your physical location. It's also not relevant to your problem.

What does "has no internet" mean?

Do you have a local IP address? "ip a"

If so, can you resolve DNS? "dig a ubuntuforums.org" or "dig a ubuntuforums.org @8.8.8.8"

If so, can you access http/s? "curl -Lfv example.com"

---

### Post by jgw on 2024-06-21
the settings in the machine that does not connect to the ethernet
it has a box titled PCI Ethernet and the cable is disconnected.
I have included a picture of this one.  I have not activated it. Don't know if I should or not.  This does not exist on the system that works. 

I am trying to send a couple of pictures so one can tell what I am talking about.  I am failing but will continue to try.  i think I got that done.  One shows my settings and the other that is on the machine that doesn't have internet and the one that works does not. Hopefully this will help.

---

### Post by jgw on 2024-06-21
I seem to have fixed the problem.   I have no idea why.  I went to the ethernet settings and created a new profile and then re-booted and, this time I have internet.  have no idea what is going on but my problem seems to be fixed.   Would have preferred understand it all but this will do.

Thank you all for the help..........

---

### Post by jgw on 2024-06-22
I have spent the entire day bringing up another machine.   The one in question is a pain.  It works, it doesn't work, back and forth, have no idea what is going on.  Once I get this other one going I will start again with that one.  I am going to have to get a list of programs I can run so somebody can, eventually, what is gong on.  I would appreciate another help with that list.

I apologize for this whole mess.

---

### Post by currentshaft on 2024-06-23
> **jgw said:**
> I have spent the entire day bringing up another machine.   The one in question is a pain.  It works, it doesn't work, back and forth, have no idea what is going on.  Once I get this other one going I will start again with that one.  I am going to have to get a list of programs I can run so somebody can, eventually, what is gong on.  I would appreciate another help with that list.

I apologize for this whole mess.

I offered four troubleshooting steps in post #4. You replied with irrelevant screenshots. Are you sure you need our help?

---

### Post by jgw on 2024-06-24
You are right and I apologize.  I ask questions, do stuff, and then suddenly its working so I claim success only to find out that was pure crap.  This time, however its going to be different and I am going to make sure before tooting my horn.  Bear with me.  I will do those that you suggested and anything else anybody wants.

Later!

---

