---
title: "Where is acpi_fakekey on 16.04?"
date: 2016-05-25
forum: General Help
---

### Post by Only1KW on 2016-05-25
I am attempting to use the acpi_fakekey executable for some keyboard remapping I am attempting to do on 16.04.  According to [http://manpages.ubuntu.com/manpages/precise/en/man1/acpi_fakekey.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/acpi_fakekey.1.html), it should be included in 16.04 as part of the acpi-support package, but I can't find it anywhere, or its manpage locally.  Anyone know where it is or how I get it?

```
$ dpkg -l acpi-support
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  acpi-support   0.142        amd64        scripts for handling many ACPI ev

```

My version installed does seem to be a slight bit newer than the online manpage.  I find it hard to believe that's the problem though.

---

