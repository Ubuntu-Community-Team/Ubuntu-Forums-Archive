---
title: "Access to Windows via VMServer"
date: 2007-04-01
forum: General Help
---

### Post by acejones on 2007-04-01
I've converted my physical windows installation to a virtual drive and I've placed it on an external hard drive on my server.  I'm able to access the directory on the server that contains the virtual drive, but I cannot get the VMWare console to connect to it.

[IMG]http://acejones.net/Screenshot.png[/IMG]

---

### Post by acormack on 2007-04-01
Is this a new vmware instalation?  

Have you ever successfully created a virual machine on the server?

In the screenshot have you actually logged in from the console onto a running vmware server?

Once connected you should be able to create the vitual machine - but if I can read the screenshot it is saying "state: disconnected"

---

### Post by acejones on 2007-04-01
> Is this a new vmware instalation?

Have you ever successfully created a virual machine on the server?

In the screenshot have you actually logged in from the console onto a running vmware server?

Once connected you should be able to create the vitual machine - but if I can read the screenshot it is saying "state: disconnected"
The VM install in Ubuntu is not new.  In fact, I had a basic XP install loaded so I could test a few things.  Then I decided I wanted to keep my XP system as is and do some more testing.  The VM install in Windows is new, but that shouldn't matter.  I've installed VM systems in the past, but this is the first time I've tried to run one remotely.  

When I run the VMServer on the Windows server to connect to the local VM XP I created, it connects.

The console does indeed say disconnected, but that is because I haven't connected it to a host yet (Local or Remote).

I guess what I'm needing is the console to show the .vmx files while browsing the server.

---

