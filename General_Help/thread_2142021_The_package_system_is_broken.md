---
title: "The package system is broken"
date: 2013-05-04
forum: General Help
---

### Post by sagent3000 on 2013-05-04
I get a pop up window when trying to install updates that says the follwoing:

> Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

Details 

The following packages have unmet dependencies:

thunderbird-globalmenu: Depends: thunderbird (= 17.0+build2-0ubuntu0.12.04.1) but 17.0.2+build1-0ubuntu0.12.04.1 is installed
thunderbird-locale-en: Depends: thunderbird (< 17.0+build2-0ubuntu0.12.04.1.1~) but 17.0.2+build1-0ubuntu0.12.04.1 is installed

when i run apt-get install -f

>  Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  thunderbird-globalmenu thunderbird-locale-en
The following packages will be upgraded:
  thunderbird-globalmenu thunderbird-locale-en
2 upgraded, 0 newly installed, 0 to remove and 337 not upgraded.
2 not fully installed or removed.
Need to get 0 B/391 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y
dpkg: dependency problems prevent configuration of thunderbird-globalmenu:
 thunderbird-globalmenu depends on thunderbird (= 17.0+build2-0ubuntu0.12.04.1); however:
  Version of thunderbird on system is 17.0.5+build1-0ubuntu0.12.04.1.
dpkg: error processing thunderbird-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of thunderbird-locale-en:
 thunderbird-locale-en depends on thunderbird (<< 17.0+build2-0ubuntu0.12.04.1.1~); however:
  Version of thunderbird on system is 17.0.5+build1-0ubuntu0.12.04.1.
dpkg: error processing thunderbird-locale-en (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 thunderbird-globalmenu
 thunderbird-locale-en
E: Sub-process /usr/bin/dpkg returned an error code (1) 

from what i am reading in the error the problem is with Thunderbird.  what is my next step?

---

### Post by grahammechanical on 2013-05-04
What version of Ubuntu are you using? Is Thunderbird installed by default? Did you install it through the Ubuntu Software Centre or through a PPA? Do you have any PPAs?

You could try un-installing Thunderbird and then re-installing if you wish to use that application.

Regards.

---

### Post by Cheesehead on 2013-05-04
How, exactly, are you upgrading? Exactly what commands or programs or process are you using?
You seem to have done something ...unusual... to get thunderbird and thunderbird-globalmenu out of sync, and to have piled up 337 unapplied updates.

The message is telling you that Thunderbird is up-to-date...but that two packages that depend upon it, thunderbird-globalmenu
thunderbird-locale-en, are too old. Did you install Thunderbird manually in the past? Or from a PPA?

How long has this problem been going on?

---

### Post by sagent3000 on 2013-05-04
> **grahammechanical said:**
> What version of Ubuntu are you using? Is Thunderbird installed by default? Did you install it through the Ubuntu Software Centre or through a PPA? Do you have any PPAs?

You could try un-installing Thunderbird and then re-installing if you wish to use that application.

Regards.

Thunderbird was installed by default when i installed Ubuntu.  I have 12.04.  No i don't think have any PPA's.   Can i just delete the thunderbird and not worry about it?

---

### Post by sagent3000 on 2013-05-04
> **Cheesehead said:**
> How, exactly, are you upgrading? Exactly what commands or programs or process are you using?
You seem to have done something ...unusual... to get thunderbird and thunderbird-globalmenu out of sync, and to have piled up 337 unapplied updates.

The message is telling you that Thunderbird is up-to-date...but that two packages that depend upon it, thunderbird-globalmenu
thunderbird-locale-en, are too old. Did you install Thunderbird manually in the past? Or from a PPA?

How long has this problem been going on?

I am updating from the Ubuntu Software center.   i have tried apt get update but get no where with that. the thunderbird was part of the default install so i haven't installed it at all.  this problem has been going on a while and i have been looking through every forum i could find and haven't found a solution yet

---

### Post by ajgreeny on 2013-05-04
Was this a clean install of ubuntu 12.04 or did you upgrade?

---

### Post by sagent3000 on 2013-05-04
> **ajgreeny said:**
> Was this a clean install of ubuntu 12.04 or did you upgrade?

this was a clean install

---

### Post by sagent3000 on 2013-05-04
i just tried 

 apt-get remove thunderbird
> 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 thunderbird-globalmenu : Depends: thunderbird (= 17.0+build2-0ubuntu0.12.04.1) but it is not going to be installed
 thunderbird-gnome-support : Depends: thunderbird (= 17.0.5+build1-0ubuntu0.12.04.1) but it is not going to be installed
 thunderbird-locale-en : Depends: thunderbird (>= 17.0+build2-0ubuntu0.12.04.1) but it is not going to be installed
                         Depends: thunderbird (< 17.0+build2-0ubuntu0.12.04.1.1~) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

---

### Post by Cheesehead on 2013-05-04
First, stop using Software Center until this is fixed. After the fix, you can start using it again.
Instead, use apt-get and the command line.

Second, in a terminal try the command "sudo apt-get update"
and post the entire result here.

---

### Post by ajgreeny on 2013-05-06
Just remove **thunderbird-globalmenu** and **thunderbird-locale-en** and see if that helps.

---

### Post by sagent3000 on 2013-05-06
okay guys i got the problem fixed.  I ended up having to synaptic package manager and manually deleting thunderbird completely off my system.  thanks for your help guys

---

