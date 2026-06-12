---
title: "Free anti virus for Linux?"
date: 2007-05-14
forum: General Help
---

### Post by danny71 on 2007-05-14
Are there free anti virus programs for Linux?

If there are, how to get them?

---

### Post by Shazaam on 2007-05-14
Four that I know of.
clamav is in Synaptic
f-prot, AVG and Avast are the others.

---

### Post by hessiess on 2007-05-14
you dont rilly need it as there arnt any viroses for linux!

---

### Post by cotcot on 2007-05-14
clamav

---

### Post by rillip on 2007-05-14
You can search for "virus" in whatever package manager/program installer you're using and probably come up with the ability to install those mentioned.

I hear very nice things about AVG, but I could never get it to work right in my install. It conintually asked me to update, then said there were no updates.  Then I couldn't get it to uninstall right.  As I understand it, clamav is mostly run from the console, which may not be for you.

I would recommend you start looking these programs up in a search engine and see what others are saying about them and making your own decision.

---

### Post by az on 2007-05-14
Note that you only need a virus scanner if you are running a mail server.

You do not need an anti virus for an Ubuntu desktop.  Just keep up-to-date with security updates.

---

### Post by Ankher on 2007-05-14
You really don't need it. Linux is built such that unless you do something really stupid, there's no way you can get a virus or have it do anything serious

[This]("http://linuxmafia.com/~rick/faq/index.php?page=virus") is an awesome explanation of why

---

### Post by happysmileman on 2007-05-14
What about windows programs running under wine? Any threat there?

---

### Post by az on 2007-05-14
> **happysmileman said:**
> What about windows programs running under wine? Any threat there?

It depends.  A virus probably won't spread.  Spyware will not really be able to install itself and run in the background, but if you are running it, it can still spy on you, theoretically.

---

### Post by GS2 on 2007-05-14
I have installed AVG and avast on systems, they run ok.
clam is on my 'server' box with cron running a scheduled scan.

If you share files with other users (email, etc) then an AV is a good idea, as the signatures will pick out any infected files you might send to a user of a different OS.

Another thing you might consider is something like rkhunter of chkrootkit for your box,, and only install packages from trusted sources.

The one drawback of a *nix system is that once someone has root privileges they can do anything on the system - root is all powerful ;)

---

