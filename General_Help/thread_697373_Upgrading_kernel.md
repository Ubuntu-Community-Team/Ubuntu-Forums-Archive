---
title: "Upgrading kernel"
date: 2008-02-15
forum: General Help
---

### Post by Wallace on 2008-02-15
I'm running Gutsy but have to run Feisty's kernel 2.6.20-16 as Gutsy's 2.6.22-14 always locks up after a few hours.

Is there a way to get apt-get to update my 2.6.20 kernel with the latest security update? 'apt-get update' only seems to want to upgrade the 2.6.22 kernel.

---

### Post by Drathas on 2008-02-15
Although I don't believe your issue with the the kernel, you can TRY looking [here](http://ubuntuforums.org/showthread.php?t=646755) to figure out how to get the newer kernel up and running.  Although I don't advise trying this as your FIRST method of debugging the problem though.

---

### Post by Wallace on 2008-02-15
Thanks, when I get some time I'll give it a go if I decide I can't wait for Hardy proper.

I think I managed to update my old Feisty kernel by switching the sources list briefly.

The 2.6.22-14 kernel has never lasted 12 hours before locking up, but 2.6.20-16 stays up for weeks on end. There's a thread on here somewhere with a load of other people who have had the same lockups. It runs fine for a while, then appears to be unable to access the HDD - every process hangs when it tries to do so, so there's no entries in the syslog to help.

---

