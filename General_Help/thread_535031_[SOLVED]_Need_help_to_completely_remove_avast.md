---
title: "[SOLVED] Need help to completely remove avast"
date: 2007-08-26
forum: General Help
---

### Post by DougieFresh4U on 2007-08-26
For some reason (stupidity) I was trying to install avast anti virus. when package installer was trying to install I kept getting messege that it could not install due to update manage or synaptic running. I know that I had neither one open so i do not know what that was about. Now the update icon is showing and when I click i get the following messege (screenshot) Please, how do I remove this or purge it or what ever needs to be done?
Please help me out with real simple instructions as I am not the "brightest bulb on the tree":(  Thanks

---

### Post by DougieFresh4U on 2007-08-26
Bump, some one please offer some magic words

---

### Post by Dark Star on 2007-08-26
Go in Synaptic In the search bar type Avast and then  a new list will appear .. right click and select mark for complete removal :) That will do if that fail try this
```
sudo atp-get remove avast   [or any other name that you need to open through Alt+F2]
```

---

### Post by isaacj87 on 2007-08-26
Well it saying that it can't find the package it self. Either locate it or re-download it. then reinstall it.

---

### Post by DougieFresh4U on 2007-08-26
thanks for quick replies.
I downloaded it again. synaptic won't open as I get this error (see screenshot) File is in temp (see screenshot). Can not remove it via terminal.

---

### Post by DougieFresh4U on 2007-08-26
Ok, got it. Heres what I did in case any one would like to know:

[B]dougie@DougiesLeanMachine:~$ sudo dpkg --force-remove-reinstreq --remove avast4workstation
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `avast4workstation' missing, assuming package has no files currently installed.
189321 files and directories currently installed.)
Removing avast4workstation .[/B]

---

### Post by isaacj87 on 2007-08-26
> **DougieFresh4U said:**
> Ok, got it. Heres what I did in case any one would like to know:

[B]dougie@DougiesLeanMachine:~$ sudo dpkg --force-remove-reinstreq --remove avast4workstation
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `avast4workstation' missing, assuming package has no files currently installed.
189321 files and directories currently installed.)
Removing avast4workstation .[/B]

Great! If you don't mind me asking (in case *I* run into future problems...where did you find out how to do this?

---

### Post by DougieFresh4U on 2007-08-26
I had a problem with IE6 a while back and a nice community member gave me instructions, which I forgot that I saved.
All I did was change package name, there for that command and what ever package that is giving drama will vanish!!

---

