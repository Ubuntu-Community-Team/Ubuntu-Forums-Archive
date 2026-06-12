---
title: "xsane doesn't detect, but sane-find-scanner does"
date: 2007-01-01
forum: General Help
---

### Post by braddcadd on 2007-01-01
_The specs:_
HP Officejet 5610 All-in-one (connected to usb)
HP thinkpad T30
Ubuntu 6.06 Dapper

_The situation:_
I have installed hplip correctly as I am told I need it.  "sane-find-scanner" detects the scanner but "scanimage -L", "xsane", and "sudo xsane" can not detect anything.  All of the sane and HP documentation say this model is supported for printing and scanning, so I must be doing something wrong.

Does anyone have any ideas on how to fight this battle?  I feel like I am close...

---

### Post by moshuptrail on 2007-01-01
I have posted the same problem to the hplip-help mail list.  It's not operated today, so I won't get an answer for a day or two.  I've got the exact same problem with an OfficeJet V40.  I've even upgrader hplip to the latest version with no relief.  I can't even get sane-find-scanner to register.  It seems to be related to the fact that the printer is identified but the scanner is not - you have to "know" there's a scanner.

If you search with Google, you'll find we aren't the only ones.  Numerous others.  But no answers.

I'll let you know if I get an answer.

---

### Post by braddcadd on 2007-01-08
Any progress yet?

---

### Post by cssutto on 2007-01-11
I have the same problem, sort of.

Xsane gives the error message that it is not able to connect with:  Then names my printer by model number, etc., and then says that there is an I/O problem.

How to fix I/O problems?

CSSJR

---

### Post by cssutto on 2007-01-11
OUCH!!!!!!!!!!


I shut the HP down and then started it again and that cured it!!!

I should know better.  That is supposed to be the first thing you do.

CSSJR

---

### Post by braddcadd on 2007-02-18
I figured out this problem (at least my version anyway).  I had two versions of hplip installed.  I installed hplip with apt-get (and no other installations of hplip) and it worked.

---

### Post by Quibly on 2007-03-03
> **cssutto said:**
> I have the same problem, sort of.

Xsane gives the error message that it is not able to connect with:  Then names my printer by model number, etc., and then says that there is an I/O problem.

How to fix I/O problems?

CSSJR

I have the exact same problem...

---

### Post by John Azelvandre on 2007-05-03
My problem is similar, but not entirely:

sane-find-scanner and scanimage -L see my scanner (an Epson Perfection 1640), but xsane freezes when I attempt to use it.  Very mysterious.  I have previously used this scanner successfully with Debian sarge, so it should work on my Edgy machine.

Any ideas?

---

### Post by matchstich on 2007-05-03
sane-find-scanner sees my epson 1200, but xsane, and all the rest freeze looking for the scanner.

have to force quit xsane--- with gimp and scanminage, i have to reboot.

---

