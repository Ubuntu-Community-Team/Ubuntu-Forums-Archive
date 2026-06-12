---
title: "error with dependencys"
date: 2017-03-29
forum: General Help
---

### Post by garymcneish on 2017-03-29
hello Im having an issue installing stuff after trying to install some intel drivers

this is the output of installs or upgrades or just about anything i try to do 

```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 libcairo2 : Depends: libfontconfig1 (>= 2.11.94) but 2.11.0-6.7+b1 is installed
             Breaks: libcairo2:i386 (!= 1.15.2-0intel1) but 1.14.8-1 is installed
 libcairo2:i386 : Breaks: libcairo2 (!= 1.14.8-1) but 1.15.2-0intel1 is installed
 libcairo2-dev : Depends: libcairo2 (= 1.14.8-1) but 1.15.2-0intel1 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```
any advise please

---

### Post by RobGoss on 2017-03-29
Hello and welcome, if you look closely at the error message it's telling you what you need to do to correct the broken packages 

Run this command below and see if that corrects your issue

```
 sudo apt --fix
```

In most cases when receiving error messages if you click details it will give you information that may help to to correct your issues

---

### Post by RobGoss on 2017-03-29
You are very welcome hope it helps

---

