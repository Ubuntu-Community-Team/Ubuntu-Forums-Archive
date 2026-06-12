---
title: "X Server issue"
date: 2007-05-29
forum: General Help
---

### Post by malkir on 2007-05-29
Whenever I try to run xserver I get the typical blue-error message and the following log:
I have an ATI Radeon X850 Platinum Edition
It's supported by xserver apparently, but:

(II) Primary Device is: PCI 01:00:0
(II) ATI:  Candidate "Device" section "ATI Technologies, Inc. Radeon X850 XT PE (R480)".
(WW) ATI:  PCI Mach64 in slot 1:0:0 could not be detected!
(WW) ATI:  PCI Mach64 in slot 1:0:1 could not be detected!
(EE) No devices detected.

to me looks like it's looking in the PCI rather than the PCI-E slot,
I tried using lspci | grep PCI but I'm not exactly sure the syntax, 
it SAYS that root PCI-E is like 0000:0:1.0 or something similar, and I can't change it to that even when configuring xserver ;[

Any ideas? This is really got me in a stump, I've been playing with it for hours


PS -- my original log is at [http://www.uberdan.com/hack/Xorg.0.log](http://www.uberdan.com/hack/Xorg.0.log)

---

