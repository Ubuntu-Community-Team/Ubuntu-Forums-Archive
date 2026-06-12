---
title: "Corrupted low memory after graphical login"
date: 2019-01-06
forum: General Help
---

### Post by lusiani-enrico on 2019-01-06
Hello everybody.
In the past few days I started seeing "Corrupted low memory" in my syslog. From other questions in various forums I know that this error is usually associated with the BIOS writing in the first 64k of memory. The difference in my case is that the error stars only after the graphical login and not during boot and that the corruption seems to be much more extensive, almost 2000 addresses vs 1/3. The error also stared appearing only in these days and I have done no modifications to the BIOS.
I have had this exact same problem one year and half ago. At the time the problem disappeared after a successful memtest (I figured that the RAM stress did something...) but now it doesn't seem to do anything (it passes).
The last time it happened, I noticed the problem after I opened an application with bumblebee and was kicked out of my X session (it does not happen this time). The log also shows nvidia as the last module unloaded before the corruption.
The only thing of note I have done on this computer lately is resizing some partitions (only data and home) and holding off the updates for a while, as update-manager was claiming that some packages could not be upgraded (among them the kernel, but apt upgrade updated it without problems so I'm not sure what the problem actually was).

Aside from the log, nothing seems to be broken. I know that I could suppress the log, but I would prefer to solve the problem, as it might be a symptom of something worse.

I'm running Ubuntu 16.04 with the hwe kernel 4.15.0-43, on a Dell Inspiron-7559, using the nvidia driver 396.54.

Here's the log from that is shown the first time. After the first it's the same, but without the last lines.
[https://paste.ubuntu.com/p/xvCSftSG93/](https://paste.ubuntu.com/p/xvCSftSG93/)

Thanks in advance.
Enrico

---

### Post by Autodave on 2019-01-06
Certainly sounds to me like a bad memory stick.  Hard to say how many are in there: looks like there are most likely 2 of them.  If there are 2 sticks, try removing the second (top?) one and try booting it.  If still same problem, remove that stick and install the previously removed one.  Try booting again.  If it now works, then likely the stick laying on your desk is the bad one.  Or, it was a dirty socket.  You could try putting it back in and see what happens.

Some sites show that as having 8 gig and some 16 gig.  If it has 16 gig, you could easily live on 8 gig unless you are running VMs or doing a lot of very heavy video editing.

---

### Post by lusiani-enrico on 2019-01-06
Thanks for the reply.
Bad RAM was my first thought too, but can memtest pass 3 times in a row with bad RAM? If it does it's much less useful than I thought.
I shall try removing the RAM this evening and hope for the best.
Enrico

---

### Post by CatKiller on 2019-01-06
Passing 3 tests isn't sufficient. Memtest works through every pattern to check the memory. That takes hours. Leaving it running overnight is recommended.

---

### Post by lusiani-enrico on 2019-01-06
I meant 3 times the whole suite of tests (10 I think?). It takes about 1h30/2h for each of the full runs

---

### Post by Autodave on 2019-01-06
If memtest says it's bad, it's bad.  If memtest says it's good......it may be good or bad.

---

### Post by lusiani-enrico on 2019-01-06
Sadly the problem persisted with either of them. 
One thing I have yet to try that would show if it's actually hardware related or caused by the software is booting from an usb stick and check if the problem persists.
I will update later with the results.
Enrico

---

### Post by Autodave on 2019-01-06
Booting from USB successfully would show that the HD is/has failed.  I really doubt that that is the problem.

---

### Post by lusiani-enrico on 2019-01-06
When booting from a live OS dmesg showed nothing.

---

### Post by lusiani-enrico on 2019-01-08
I don't think I understand what you mean. Are you saying that if the Live OS showed no problems (and it does not) the problem might be related to a failing HD?
Enrico

---

