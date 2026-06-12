---
title: "Please help me install Brother QL-500 label-printer"
date: 2008-05-21
forum: General Help
---

### Post by Andre-D on 2008-05-21
Please help, I have Brother's Linux drivers, and can't make them work on my 8.04:

got my drivers from: [http://welcome.solutions.brother.com/bsc/public_s/es/os/linux/index.html](http://welcome.solutions.brother.com/bsc/public_s/es/os/linux/index.html)

I do (as instructions say I should:)

sudo dpkg -i --force-all ql500lpr-1.0.0-1.i386.deb

This goes as brother says it should, now:

dpkg -i --force-all ql500cupswrapper-1.0.0-1.debian.i386.deb

some errors..

```
(Reading database ... 156073 files and directories currently installed.)
Preparing to replace ql500lpr 1.0.0-1 (using ql500lpr-1.0.0-1.i386.deb) ...
Unpacking replacement ql500lpr ...
Setting up ql500lpr (1.0.0-1) ...

andre@Ubuntu:~/Documents/QL-500$ dpkg -i --force-all ql500cupswrapper-1.0.0-1.debian.i386.deb
dpkg: operation requires read/write access to dpkg status area
andre@Ubuntu:~/Documents/QL-500$ sudo dpkg -i --force-all ql500cupswrapper-1.0.0-1.debian.i386.deb
Selecting previously deselected package ql500cupswrapper.
dpkg: regarding ql500cupswrapper-1.0.0-1.debian.i386.deb containing ql500cupswrapper:
 ql500cupswrapper conflicts with ql500cupswrapperinch
  ql500cupswrapperinch (version 1.0.0-1) is present and installed.
dpkg: warning - ignoring conflict, may proceed anyway !
dpkg: regarding ql500cupswrapper-1.0.0-1.debian.i386.deb containing ql500cupswrapper:
 ql500cupswrapperinch conflicts with ql500cupswrapper
  ql500cupswrapper (version 1.0.0-1) is to be installed.
dpkg: warning - ignoring conflict, may proceed anyway !
(Reading database ... 156073 files and directories currently installed.)
Unpacking ql500cupswrapper (from ql500cupswrapper-1.0.0-1.debian.i386.deb) ...
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/local/Brother/PTouch/ql500/cupswrapper/brcupsconfpt1', which is also in package ql500cupswrapperinch
dpkg - warning, overriding problem because --force enabled:
 trying to overwrite `/usr/local/Brother/PTouch/ql500/cupswrapper/cupswrapperql500pt1', which is also in package ql500cupswrapperinch
(Noting disappearance of ql500cupswrapperinch, which has been completely replaced.)
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 
Setting up ql500cupswrapper (1.0.0-1) ...
/var/lib/dpkg/info/ql500cupswrapper.postinst: 3: /usr/local/Brother/PTouch/ql500/cupswrapper/cupswrapperql500pt1: not found
 * Restarting Common Unix Printing System: cupsd                         [ OK ] 

```

This results in an "almost" success, results in printer installed, but not being able to print , because CUPS only thinks it can print the "legal" page format (and it's a label printer).

Please help.

---

