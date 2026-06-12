---
title: "Kdevelop makefile issues -- system clock invalid"
date: 2007-03-07
forum: General Help
---

### Post by Dxh on 2007-03-07
When I try to build or compile anything in Kdevelop, I get pretty far along the process until the very end (or seemingly so), when it checks for the sanity of the system, at which point it tells me the following:

checking whether build environment is sane... 
configure: error: ls -t appears to fail. Make sure there is not a broken
alias in your environment
configure: error: newly created file is older than distributed files!
Check your system clock

The error is, thankfully, obvious, but I am uncertain as to what I need to configure to make this work. My BIOS clock IS correct, as is Ubuntu's system clock... So, is Kdev configured wrong?

Any help? Should I just rebuild Kdev?

---

### Post by Dxh on 2007-03-08
Anyone?

---

### Post by dsclee on 2007-03-19
Hi Ya,

I just signed up to these forums just to tell you the answer because its been p*ssing me off for 3 hours!!

Its nothing to do with what you think it is.... You need to change the path to the file so it has no spaces.

In my case it had "home\Uni Stuff\" in the path and created the same annoying error.

Hope this of help to you!! :)

---

