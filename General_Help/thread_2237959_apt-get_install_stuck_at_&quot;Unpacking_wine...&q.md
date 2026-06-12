---
title: "apt-get install stuck at &quot;Unpacking wine...&quot;"
date: 2014-08-04
forum: General Help
---

### Post by web_knows on 2014-08-04
Hello,

I'm running Ubuntu 14.04 LTS and using an ordinary apt-get install playonlinux command to have it installed.

However, it is always getting stuck at:

```
Preparing to unpack .../wine1.6-amd64_1%3a1.6.2-0ubuntu4_amd64.deb ...
Unpacking wine1.6-amd64 (1:1.6.2-0ubuntu4) over (1:1.6.2-0ubuntu4) ...
```

I have already tried running apt-get [auto]clean, apt-get update, also tried manually downloading from a different mirror and installing the package manually with dpkg -i, but all those attempts had the same outcome: stuck at Unpacking wine1.6-amd64.

Running sudo apt-get -f install or sudo dpkg --configure -a due to the broken earlier installation didn't help either. And now looks like the 2 wine packages on my system are in a very inconsistent shape:

```
thatGuy@Neverland:/var$ dpkg -l wine1.6*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-==============================================================================
iU  wine1.6                              1:1.6.2-0ubuntu4        amd64                   Microsoft Windows Compatibility Layer (Binary Emulator and Library)
iHR wine1.6-amd64                        1:1.6.2-0ubuntu4        amd64                   (no description available)
rHR wine1.6-i386                         1:1.6.2-0ubuntu4        i386                    Microsoft Windows Compatibility Layer (32-bit support)
```

Please help saving my bacon!

Thanks,
- R

---

### Post by web_knows on 2014-08-06
Bump?

---

### Post by kc1di on 2014-08-06
do the following in a terminal and try installing again.
```
sudo dpkg --configure -a
```
Then run the following.
```
sudo apt-get clean && sudo apt-get autoclean
```

---

### Post by web_knows on 2014-08-07
I did. Got this:

```
thatGuy@Neverland:~$ sudo dpkg --configure -a
[sudo] password for thatGuy: 
dpkg: dependency problems prevent configuration of wine1.6:
 wine1.6 depends on wine1.6-amd64 (= 1:1.6.2-0ubuntu4); however:
  Package wine1.6-amd64 is not installed.
 wine1.6 depends on wine1.6-i386 (= 1:1.6.2-0ubuntu4); however:
  Package wine1.6-i386 is not installed.

dpkg: error processing package wine1.6 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wine1.6
```

---

### Post by web_knows on 2014-08-07
This is the status of the wine packages on the system (these are the only ones that are related to wine and are not in an "ii" status):

```
iU  wine1.6                                               1:1.6.2-0ubuntu4                                    amd64        Microsoft Windows Compatibility Layer (Binary Emulator and Library)
iU  wine1.6-amd64                                         1:1.6.2-0ubuntu4                                    amd64        Microsoft Windows Compatibility Layer (64-bit support)
pHR wine1.6-i386                                          1:1.6.2-0ubuntu4                                    i386         Microsoft Windows Compatibility Layer (32-bit support)
```

What should I do to get them back into shape?

---

### Post by kc1di on 2014-08-08
I would uninstall wine and attempt a reinstall.
```
sudo apt-get purge wine
```

Then do an autoclean and try again.

---

