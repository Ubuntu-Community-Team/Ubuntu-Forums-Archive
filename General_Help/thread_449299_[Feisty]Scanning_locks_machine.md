---
title: "[Feisty]Scanning locks machine"
date: 2007-05-20
forum: General Help
---

### Post by der_vegi on 2007-05-20
Hi everyone!

I've got an old i386 machine here and have just installed Feisty these days. But scanning is a problem. Yeah, there is this known bug with the black image scan and there are workaraounds for that. But I have a different problem: Scanning locks my machine so that the only thing I can do is to reboot.
```
scanimage -L
``` gives me
```
Segmentation fault (core dumped)
```
Kooka crashes immediately at startup and Xsane gives me a strange warning message at the beginning: "You try to run XSane as ROOT, that really is DANGEROUS!" though I don't run it as sudo. I can click on "continue at your own risk" and then the application starts, freezing my system when I start scanning. In console I have also the option tu run xsane.bin, which also crashes with segmentation fault. So maybe the start of xsane runs a script that starts it as sudo? But acutally I don't care about the warning.

```
sudo scanimage -L
``` sometimes gives me the scanner ID, sometimes freezes my machine as well.

Any idea? Thanks for the help!

---

### Post by der_vegi on 2007-05-20
Strange. I just discovered that my scanner works in the "Unified Driver Configrator" Tool (Version Common 2.00.95), that came with the installation of the Samsung CLP 510 printer. This is a tool where you can manage your printers and scanners...

---

