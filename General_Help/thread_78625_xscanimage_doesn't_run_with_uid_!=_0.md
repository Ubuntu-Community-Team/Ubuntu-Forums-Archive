---
title: "xscanimage doesn't run with uid != 0"
date: 2005-10-18
forum: General Help
---

### Post by m87 on 2005-10-18
i've spent my last hour getting my scanner working. it was REALLY easy, just some package to install, BUT no normal user can use it.

```
marco@pride: ~ $ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
marco@pride: ~ $

```

and of course

```
pride ~ # scanimage -L
device `epson:libusb:003:015' is a Epson GT-X700 flatbed scanner
device `epkowa:libusb:003:015' is a Epson Perfection 4870 flatbed scanner
pride ~ #

```

any ideas?

it's not a matter of device node because it doesn't use any, don't ask me why :confused:

---

