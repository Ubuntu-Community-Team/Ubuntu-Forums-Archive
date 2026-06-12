---
title: "How to get a bug fixed."
date: 2017-01-23
forum: General Help
---

### Post by moteprime on 2017-01-23
Hi.
For a long time i have had this silly bug in Ubuntu, i have to kill and restart nm-applet in terminal every time that my Thinkpad comes back from suspend because it somehow crashes. There's several bug reports with many users affected on Launchpad but it doesn't get attention from anybody capable of actually getting it fixed.
How can we get it on the right way?



Here's a couple of the reports:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1636282](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1636282)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1589401](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1589401)
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574347](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1574347)

---

### Post by ian-weisser on 2017-01-23
The correct way is described by seb128 (a Canonical engineer) in [comment #10 of bug 1589401]("https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/1589401/comments/10").
Several bugs have received Triage from both paid engineers and highly-qualified volunteers. Not being ignored at all.

A bug report must describe the problem in sufficient detail so that a Triager or Developer can replicate the problem on their machine. I've done Triage and I've written patches - if I cannot make the problem happen on my test system, then I cannot determine the cause and fix it. It's that simple.

Developers fix bugs that are both high-priority and super-easy first. You, the sufferers, can affect both of those.

Make a bug higher priority by searching for similar sufferers. Make sure they *really* suffer from the same bug ('close' is not close enough - a different bug is a different bug), then subscribe them to the bug report.

Make the bug super-easy to fix by keeping the bug report clean, upstreaming the bug to the correct projects, agreeing on a single technical definition of the bug, and researching/testing which part of the software stack the bug resides in.

You don't need to do any of those, of course. If you wish to be completely at the mercy of the volunteer Triage community, that's entirely your decision. Most volunteer Triagers, being human, work the easy ones first.

---

### Post by moteprime on 2017-01-23
I did report the bug upstream as suggested, but i am just a user that's not skilled enough technically to follow up on it. (Don't know about Triaging at all). At the bugzilla and launchpad report other users  comment, change the title, description and other settings, and i don't know what to do, how to, or if I'm even supposed do anything. It's very frustrating.
I can see lot's people all over the internet describing this as widespread bug in Ubuntu 16.04, I'm just sad that it's not being addressed by anybody.

---

### Post by vasa1 on 2017-01-23
> **moteprime said:**
> ... (Don't know about Triaging at all). ...

Here's a nice read: [http://nedbatchelder.com/text/triaging.html](http://nedbatchelder.com/text/triaging.html)

I found it by googling for ***triaging bugs***.

---

### Post by ian-weisser on 2017-01-23
> **moteprime said:**
> i am just a user that's not skilled enough technically to follow up on it.
Nobody is born with the technical skills. Everybody who learned them started from precisely the position you are in - a problem that they don't really understand and nobody else seemed to care about.

This is the Free Software ecosystem - you get the software free, and in exchange you contribute improvements: Better code, triaged bugs, documentation, support help, etc.

Many of the tasks that would make the bug easier and faster to fix are not technical at all, or are rather easy to learn.
The bug will be fixed faster when somebody is willing to spend a bit of time and learn them.

If you are willing, we can show you the next steps and start you down the path of learning. It's not difficult.
If you merely wanted a sympathetic ear, and want someone else to learn the skills and do the legwork, then please mark the thread as [solved].

---

### Post by moteprime on 2017-01-23
@ian-weisser It's not about getting somebody else to do the work, i'll do what i can. I test for the qa team and report when i have time, help others when i can (not much on this forum though), if you'll help me get this bug on it's way i'll say thank you.

---

### Post by ian-weisser on 2017-01-23
> **moteprime said:**
> I test for the qa team and report when i have time

Thank you for testing!
Thank you for providing support!
 
I just looked at the Upstream bug ([https://bugzilla.gnome.org/show_bug.cgi?id=767317](https://bugzilla.gnome.org/show_bug.cgi?id=767317))

I see where a Gnome engineer has asked three times for help testing and additional information, with only one partial reply.
Not much the developer can do until they receive all the information they have asked for.

This is how you make it super-easy for the Developer to fix the bug: Don't make them ask twice for information. Recruit good testers and reporters from among the community of sufferers. Don't make the developer dig around multiple websites and places for information. Pick a primary bug report (usually the upstream report), and point to it from everywhere else. Share information among the various bug reports. Be cheerful and positive in all written communication so Developers want to come back to your bug.

Those are not technical skills. They are, in fact, leadership skills. The Developer is the Technical Expert, not the leader. Anyone in the community can lead the bug toward 'Fix Released' status.

---

### Post by moteprime on 2017-01-24
@ian-weisser - I apologise for not replying, i have not had spare time. Will do tomorrow.

---

### Post by HermanAB on 2017-01-24
There is also the middle way - finding a workaround to use until the bug gets fixed.

For example, anything that can be done manually on a computer, can be automated on the same computer.  Therefore it is feasible to automatically restart nm aplet when the PC returns from suspend.  However, since I'm not running Ubuntu on a laptop and never use Ubuntu suspend, I cannot easily research that angle.  Someone else may be able to tell you how though.

---

### Post by moteprime on 2017-01-25
@ian-weisser
Reading through the bug in bugzilla again i can see that i hoped someone else (in my mind better qualified) would take over. (I'm 'mote' that reported to bugzilla.

But one makes a patch, Galvani (that seem to understand better than me) dismisses it.
In comment #27 [https://bugzilla.gnome.org/show_bug.cgi?id=767317#c27](https://bugzilla.gnome.org/show_bug.cgi?id=767317#c27)
Another (a Dane actually) has found out that the bug are dependant on "All users may connect to this network", i tried it and the applet doesn't crash when this option are tagged, so he's unto something, so what do you suggest i do. Confirm that from other 'sufferes' on launchpad, or should i pickup on the patch. (i'm not skilled enough to test that myself)

Please no need to thank me for testing, it's what i can do. I tried translating, but it's way more difficult than anybody that hasn't tried can imagine.

---

### Post by moteprime on 2017-01-25
@HermanAB Thank you, and yes. But it's not really the same as getting it done proper is it. ;-))

---

