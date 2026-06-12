---
title: "Unable to Setup Local Printer"
date: 2008-02-17
forum: General Help
---

### Post by posaune on 2008-02-17
Howdy,

This'll be my first post so apologies if I make mistakes ...

I'm using a desktop that dual boots into either Ubuntu 7.10 or Windows XP.

I'd like to add a new, local printer and choose System > Administration > Printing, then "New Printer".

I then encounter two problems:

1) the Printer configuration utility fails to detect the printer plugged into the parallel port
2) if I then try to manually configure a connection on LPT 1 for my Kyocera FS-800, when I try to apply the changes, I'm prompted for a password which is never accepted.

Under Windows, the same hardware is able to successfully detect and print to this printer, so I'm confident all the physical side of it is connected properly.

An ideas why Printer config can't "see" the printer and gets stuck in a password loop?

Thanks,
James

---

### Post by posaune on 2008-02-17
Or, indeed, are there any ways I can get some debug on this?

Ta, James

---

### Post by posaune on 2008-02-18
Or, indeed, where else I could look for support ...

James

---

### Post by posaune on 2008-02-26
Ho hum :(

---

### Post by posaune on 2008-05-11
Well, Hardy Heron brings an improvement - the printer is now detected.

However, the password prompt loop problem still persists.

---

### Post by twright on 2008-06-01
you can see any debug info using system/administration/system log

try looking there while the printer is being connected (and post anything you see referring to the printer/cups)

---

