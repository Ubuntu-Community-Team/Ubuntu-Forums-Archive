---
title: "Lice CD Usage"
date: 2007-01-30
forum: General Help
---

### Post by TheMG on 2007-01-30
I tried to run it off the live CD, I choose start/install, it loads, then goes into the black screen with flashing underscore, but then it displays a message about the misconfigured X server, and directly below it says about sudo commands and warrantys, and has a command prompt (these are displayed without me touching a button). But this message is wrapped outside of the screen. What shall I do?

---

### Post by muguwmp67 on 2007-01-30
Which version of the 'live' cd are you using?  What kind of hardware are you using?  I had problems running the 6.10 x64 live cd on my amd64 desktop.  The x386 version worked fine though.

---

### Post by TheMG on 2007-01-30
AMD Athlon 64 3800+
ATI Radeon X850
v6.06.1 X64

---

### Post by muguwmp67 on 2007-01-30
I had problems running the 64 bit too on my amd.  Safe mode worked, I think, but ultimately I went with the 386 version.  The generic kernel supports SMP, so it still uses the full power of your CPU.  

For right now I chose the 32-bit version because:
- It installed without needing any install switches
-Some binaries aren't compatible with 64-bit, and its a PITA to have to compile everything.  And sometimes the source isn't available (Neverwinter Nights).

---

