---
title: "Broken packages - Cannot install aptitude???"
date: 2007-02-26
forum: General Help
---

### Post by strabes on 2007-02-26
I am on an almost brand new install of kubuntu feisty herd 4. I run "sudo aptitude dist-upgrade" and something happens. Now, apparently aptitude is not installed and I get this:

> 
alex@alex-laptop:~$ sudo apt-get install aptitude
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  aptitude: Depends: libapt-pkg-libc6.4-6-3.53
E: Broken packages
alex@alex-laptop:~$ 

> 
alex@alex-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
alex@alex-laptop:~$ 


I am particularly concerned with the line "This may mean that...if you are using the unstable
distribution that some required packages have not yet been created or been moved out of Incoming."

Is this just because I'm using feisty? If so, will my problem be resolved in the month leading up to the release of feisty?

Thanks for any help you can give me.

---

### Post by nereid on 2007-02-26
It could be a problem related to Feisty. But aptitude should be allready installed by default, shouldn't it?

---

### Post by strabes on 2007-02-26
aptitude is installed by default, but it uninstalled itself in order to fix some dependency problem. I still have apt get, but it keeps holding back the two packages apt and apt-utils for some reason...

---

### Post by nereid on 2007-02-27
Can you reinstall apt-get? Maybe something like that would solve your problem or reinstalling the mentioned lib from above: libapt-pkg-libc6.4-6-3.53?

---

