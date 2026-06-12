---
title: "ClamAV weirdness"
date: 2007-05-14
forum: General Help
---

### Post by p_quarles on 2007-05-14
I did a quick search on the forums and didn't find anyone else with this problem, but forgive me if I overlooked it.

Initially I installed the ClamTK UI. When I tried to run a scan, it told me my definitions were out of date. So, I tried to update them, and got a message telling me I couldn't. So, I uninstalled the whole suite, and reinstalled it from the terminal. 

I ran a scan, which immediately told me (again) that my definitions were out of date. Still, the scan found three trojans in my e-mail directories. I told it to sudo freshclam, and a few seconds later it told me that everything was up to date. I ran the scan again, this time telling it to quarantine the detections. Again, I get a message saying "The virus database is older than 7 days. Please update it immediately!"

Also, when I initially said freshclam, it returned "ERROR: Can't open /var/log/clamav/freshclam.log in append mode (check permissions!)." Then I said sudo and entered my password and it told me it was up to date, only to contradicted by another message seconds later.

Any ideas? I'm not worried about the Windows-targeted trojans, I just want to be able to set this up so I can update the virus database. Thanks in advance.

---

### Post by cor2y on 2007-05-18
One user suggested that you download and install the latest version of clamtk from sourceforge version 2.32 there is a deb available there if you don't want to compile from the source.
It works and stops delivering the error about updating your virus definitions.
Get it here [http://sourceforge.net/projects/clamtk/](http://sourceforge.net/projects/clamtk/)

---

### Post by p_quarles on 2007-05-19
I tried your suggestion, cor2y, and I got the same messages (library is out of date, log error when I try to use freshclam). I should mention that ClamTK did NOT give me these messages itself, but they showed up in the terminal window which I happened to have open. Any further ideas still appreciated!

5/20 edit: Nevermind, I'm an idiot. When I did that, I forgot to use "sudo," so of course it gave me an error message (updating the definitions is a root action). When that occurred to me, I did it again (correctly, this time) and did NOT get the command line error message that I got the previous time. Which is all to say: thanks for your help!

---

### Post by Blind Tiger on 2007-09-17
I just did a ClamAv and ClamTK install on Ubuntu Studio 1.0 and experienced the same issue, plus an additional weirdness involving clamav not being able to find definitions.  I'm going to try to install the latest ClamTK to see if that solves the problem.

---update---
I updated to the latest ClamTK via a .deb install (e.g. not via synaptic) and this solved the errors i was experiencing.

---

