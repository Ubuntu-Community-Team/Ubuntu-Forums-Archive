---
title: "Fancontrol -&gt; after long suspend they don't start - 12.10"
date: 2013-05-23
forum: General Help
---

### Post by tudstudent on 2013-05-23
All, i hope someone can help me investigate this issue, because it ennoys me a lot...

I have a small HTPC with an atom, unfortunately an Atom is incapable of doing frequency scaling (d-series). But there is a PWM fan inside so I decide to configure the PWM config (lm-sensors). It first complained about automaticaly setup, so I disabled everything in the bios -> no control here anymore plus there was an option to check if the fan is running -> also disabled.

So the bios does not control the fan anymore.

When I booted the system all works fine, fan is nicely quiet just as setup. However after suspend it was running at max speed. Seems this is an persistant bug in the kernel:
[https://bugzilla.redhat.com/show_bug.cgi?id=895276](https://bugzilla.redhat.com/show_bug.cgi?id=895276)

From here I used commit 26 - and created the file which is run after suspend.
This works good for a short suspend. Then this is executed (lets say a pause of 1 hour ->guessing) But after a night sleep 7-10 hours it is not executed. In the suspend log I see the line, but no execution stopping sensors - starting sensors.

Problem on the kernel log:
[https://bugzilla.kernel.org/show_bug.cgi?id=58311](https://bugzilla.kernel.org/show_bug.cgi?id=58311)

Here the problem is discussed as well:
[https://bugzilla.kernel.org/show_bug.cgi?id=58301#c3](https://bugzilla.kernel.org/show_bug.cgi?id=58301#c3)

So however the items are discussed to make a complete solution it is not there yet....
So at least I know the resume/restart of fancontrol is not started, because it is may be??? executed to early during suspend resume?
(Btw: I am using the latest stable kernel -> kernel 3.9.2)

Hope my question is clear and someone can help me with an answer...

---

