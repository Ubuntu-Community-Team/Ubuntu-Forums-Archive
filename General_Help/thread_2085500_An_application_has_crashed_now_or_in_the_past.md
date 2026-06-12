---
title: "An application has crashed now or in the past"
date: 2012-11-18
forum: General Help
---

### Post by bill-lancaster on 2012-11-18
I get this message at every boot.

How can I find what's causing it?

Ubuntu 12.04
KDE 4.9.2

---

### Post by PaulW2U on 2012-11-18
Is there anything in /var/crash that gives an indication as to what the source of the crash report might be?

Take note of the time/date stamps on the .crash files. The crashes may have happened on shut-down but could not be reported until the system was restarted.

---

### Post by bill-lancaster on 2012-11-19
Thanks, yes I have

_usr_bin_nepomukservicestub.1000.crash timed at yeserdays close down.

But have just closed then booted the system.

Crash notification as usual but nothing new in /var/crash/

What now?

---

### Post by bill-lancaster on 2012-11-20
Decided to remove the files in /var/crash/.

No more notification when booting.

---

