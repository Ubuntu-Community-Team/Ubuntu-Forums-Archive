---
title: "Changing the SSH login message"
date: 2007-01-10
forum: General Help
---

### Post by Devilotx on 2007-01-10
When I connect to my Linux server with Putty or bash, I see this:

Linux *********** 2.6.15-27-386 #1 PREEMPT Fri Dec 8 17:51:56 UTC 2006 i686 GNU/Linux

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

I'd like to change that to say something else, like to announce the machine and bash alias's I've defined.

Is this possible?

---

### Post by Olav on 2007-01-10
> **Devilotx said:**
> When I connect to my Linux server with Putty or bash, I see this:

(stuff)

I'd like to change that to say something else, like to announce the machine and bash alias's I've defined.

Is this possible?
Of course, try editing /etc/motd

---

### Post by Devilotx on 2007-01-10
Oh perfect!!!!

Thank you very much, worked perfectly:

---

