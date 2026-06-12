---
title: "[SOLVED] hardy scanner problem"
date: 2008-05-17
forum: General Help
---

### Post by Eraser007 on 2008-05-17
Hi,


Recently I've upgraded from Gutsy to Hardy, all works perfect except my scanner (HP Scanjet 7400c). In Gutsy there were no problems at all.

When I'm trying to scan a document with xsane (0.995) or any other program I'm getting a 'segmentation fault' and the application exits.

ScanImage -L returns:
device `avision:libusb:002:002' is a Hewlett-Packard ScanJet 7400c flatbed scanner
So the scanner is being found.

Running xsane as normal user or as root doesn't make a difference at all, so no permission problem.

I've added my user to the usergroup 'scanner' but still I couldn't scan.

Everytime the application exits, a new entry is added to the log:
 scanimage: io/hpmud/pp.c 627: unable to read device-id ret=-1
or
 xsane: io/hpmud/pp.c 627: unable to read device-id ret=-1  

Does this problem seem familiar to someone? 
Any help is welcome.

Kind Regards

---

### Post by Eraser007 on 2008-05-18
Hi,

I've solved the problem.
In case someone has the same error, here my solution:

After running xsane using gdb I discovered the error was caused by libsane 1.0.19.
I've downgraded back to 1.0.18 and my scanner works perfect.

Hopefully it helps

Kind regards

---

### Post by dumpster25 on 2009-05-28
> **Eraser007 said:**
> Hi,

I've solved the problem.
In case someone has the same error, here my solution:

After running xsane using gdb I discovered the error was caused by libsane 1.0.19.
I've downgraded back to 1.0.18 and my scanner works perfect.


**How exactly did you downgrade? ** :(
I'm having a similar error but with the as6e scanner driver. I'm getting the same error. I'm running Jaunty though but it seems it's the same version of the library.

---

