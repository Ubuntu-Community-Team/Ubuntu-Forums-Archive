---
title: "messed up my ubuntu .... help needed!!!"
date: 2007-07-04
forum: General Help
---

### Post by @vijay@ on 2007-07-04
recently  i got  a new conexant hsf  modem and tried to install driver for it and installed the deb file from
[http://www.surak.eti.br/linux/ubuntu/deb/conexant/](http://www.surak.eti.br/linux/ubuntu/deb/conexant/)

i got some strange errors .............. i uploaded the file


NOW THE PROBLEM IS

when ever i tried to remove the package im getting the following error
---------------------------------------------------------------
Writing extended state information... Done
dpkg: error processing conexant (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 conexant
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
-----------------------------------------------------------------
i even tried dpkg --force-all remove conexant & aptitude install -f but cant remove


when ever i open synaptic manager im getting the error showed in the screenshot

anyone plz help cant install anything or remove:(:( ......... im totally clueless

---

### Post by divague on 2007-07-04
try this:

$sudo apt-get install -f

this helped me once.

---

### Post by @vijay@ on 2007-07-04
thanx for the reply; i tried it already ,but no use

---

### Post by dabl on 2007-07-04
Try ```
sudo dpkg --configure -a
```

If that seems to restore your apt package manager, then do the following:

```
sudo apt-get autoclean
```

```
sudo apt-get autoremove
```

and you should be back in business. If not, there's something seriously damaged ...

:neutral:

---

### Post by altonbr on 2007-07-04
Looks similar to my problem: [http://ubuntuforums.org/showthread.php?p=2962742](http://ubuntuforums.org/showthread.php?p=2962742)

Haven't found a solution yet though.

---

### Post by @vijay@ on 2007-07-05
@dabl 
i will try it and will inform u ..........

@altonbr
looks like exactly same prob for u too ............. plz tell me if u find a solution:(:(

---

### Post by @vijay@ on 2007-07-09
@dabl 
tried that but no use 

any ideas ????

---

### Post by marsbt on 2007-07-09
@vijay@ - what do you get with the following command (in terminal)
> dpkg -l *conexant*

---

### Post by @vijay@ on 2007-07-11
here is the output i got when issued the command   dpkg -l *conexant*

fvijay@vijay-desktop:~$ dpkg -l *conexant*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
iHR conexant       192-1ubuntu-1  modem modules for conexant hsf models
fvijay@vijay-desktop:~$

---

### Post by altonbr on 2007-07-11
Suggestion a guy gave me (and worked): [http://ubuntuforums.org/showpost.php?p=2973000&postcount=9](http://ubuntuforums.org/showpost.php?p=2973000&postcount=9)

I searched for my specific "mfc8440lpr" package. Make sure you only search and delete the EXACT package that  is causing you problems.

---

### Post by @vijay@ on 2007-07-12
will try and inform u 
i hope it works for me too :(

---

### Post by @vijay@ on 2007-07-12
@altonbr

 thanx alot it worked :guitar::guitar::guitar:
solved my problem now:lolflag:

---

