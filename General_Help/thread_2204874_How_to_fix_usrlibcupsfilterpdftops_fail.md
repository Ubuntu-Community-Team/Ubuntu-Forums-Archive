---
title: "How to fix /usr/lib/cups/filter/pdftops fail ?"
date: 2014-02-10
forum: General Help
---

### Post by cigtoxdoc on 2014-02-10
I have three PCs on my desk.  All feed two Brother MFC-9440CN printer/scanners using USB connections and TrippLite USB switches.  All PCs running 12.04 64-bit.  Two of three PCs work well with both MFC devices doing PDF printing.  All three work well on scannning from both MFCs.  One PC keeps giving /usr/lib/cups/filter/pdftops fail errors when printing PDF, but not character-based documents.  Same error coccurs when using cups-pdf to print to file.  Offending PC is hp/compaq dx2250M dating from 2007.  Win XP side works fine, and this PC has printed PDFs from Ubuntu 12.04 64-bit before.

John

---

### Post by cigtoxdoc on 2014-03-14
My PC still WILL NOT PRINT PDF DOCUMENTS

I have followed troubleshooting suggestion including purging cups-pdf, reinstalling, and restarting.

What does the following message mean?

john@john-dx2250M:~$ service cups restart
stop: Rejected send message, 1 matched rules; type="method_call", sender=":1.425" (uid=1000 pid=25656 comm="stop cups ") interface="com.ubuntu.Upstart0_6.Job" member="Stop" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")
start: Rejected send message, 1 matched rules; type="method_call", sender=":1.426" (uid=1000 pid=25653 comm="start cups ") interface="com.ubuntu.Upstart0_6.Job" member="Start" error name="(unset)" requested_reply="0" destination="com.ubuntu.Upstart" (uid=0 pid=1 comm="/sbin/init")

---

### Post by steeldriver on 2014-03-14
those errors are probably because you need elevated (root) permissions to restart the service

```
**sudo** service cups restart
```

---

### Post by cigtoxdoc on 2014-03-19
Thank you for your reply

So far that has not solved problem.  The printer (Brother MFC-9440CN) self-test page (characters only) will print.  The Ubuntu print test page will not.  I am at a lost on what to do next.

John

---

### Post by cigtoxdoc on 2014-04-25
This problem was solved by one of the experts at experts-exchange.com .  Following his instructions, I had to create an error log using strace.  He used that file to identify that file permissions for tmp were not correct and temporary files used for printing some documents using both cups-pdf and the Brother MFC-9440CN could not be created.  I used konqueror running in the super user mode to correct the file permissions.

John

---

