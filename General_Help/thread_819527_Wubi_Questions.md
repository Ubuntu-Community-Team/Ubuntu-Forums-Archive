---
title: "Wubi Questions"
date: 2008-06-05
forum: General Help
---

### Post by timofthec on 2008-06-05
Apologies if these questions have been asked elswhere, although they are pretty specific to my needs.

I use Ubuntu at home but am stuck with Windows XP at work.  I had tried Ubuntu on a pen drive but the computer at work does not support booting from a usb device and was seraching the forums for another solution when I found Wubi :)

My questions are: - 

1. If I create a restore point in XP and have problems with the Wubi installation, will I still be able to get into XP Safe Mode and restore the system?  I ask as some people appear to have problems with the installation - don't wana break the computer at work :)

2. Can I get the whole download without using the Wubi Installer?  At the moment, it seems that I have to launch the installer and wait over an hour for it to downlaod the software as part of the instalation process - can't be doing that at work.  Hoping I can download it at home and then load it of a 4gb pendrive and install it from there.

Thanks

Tim

---

### Post by uidb4056 on 2008-06-05
1. You can do a restore point before install Wubi but I don't think you will have a problem with the installation.

2. You can download the Live CD of ubuntu (at least the live CD of 8.04 includes Wubi on it) then at work with XP running start the autorun of CD if not starts automatically an a Wizard to install Wubi will appear, follow it and you will end with Wubi installed. If later on you would like to uninstall it you can go on XP to Add/Remove programs and select to remove it. Wubi install will not have to affect your XP config it only uses a free space in your disk and add a boot option for Ubuntu in boot.ini on your XP.

---

### Post by timofthec on 2008-06-05
Thanx for that Uidb - will take me ubuntu disk with me tomorrow and try it out :)

---

### Post by deltaprime on 2008-06-05
you can even get a free cd from ubuntu, they mail it to you pretty fast and its completely free (no handling, shipping - NOTHING)
Its pretty cool. That way you can have a nice copy of ubuntu just in case youll need it and you can get rid of the cd that you scribbled Ubuntu 8.04 Desktop edition on :lolflag:
i suggest you try live cd first. Install is always smooth never had any problems.
remember google and this forum are your best friends 

delta

---

### Post by Paqman on 2008-06-06
> **timofthec said:**
> Thanx for that Uidb - will take me ubuntu disk with me tomorrow and try it out :)

You'll need to have admin rights on the machine to use Wubi.

---

### Post by timofthec on 2008-06-09
Ok, following on from above, I have installed wubi on me pc at work without any problems :)

The next step is that I MUST use Excel and have been looking to do this  through Wine.  I installed, MS office on my home computer with wine (I run Hardy) at the weekend to practise setting it up but I keep getting what appears to be a common error with the latest version of Wine re: the programme continually asks for the serial number and will not run.

I have done a bit of forum reading and the best advice seems to be to install version 0.9.53 of wine, in which, office seems to work best.  I have been on the Wine download archive but version 0.9.53 is recorded as working under Gutsy - see here [http://wine.budgetdedicated.com/archive/index.html](http://wine.budgetdedicated.com/archive/index.html)

my question is, will this old version of Wine run in wubi?  At work, I don't really get the time to experiment with this, so, any input appreciated.

---

### Post by ago on 2008-06-09
Other than for disk access, a Wubi installation is identical to a normal one for all intent and purposes

---

### Post by timofthec on 2008-06-09
QUOTE=ago;5148546]Other than for disk access, a Wubi installation is identical to a normal one for all intent and purposes[/QUOTE]

Thanx for that ago.

I downloaded and attempted to run wine ver 0.9.53, however, I get the following error in wubi when I ran the package: -

> Error: Dependency is not satisfiable: libldap2

Is there something else that I need to do?

Not sure if this is linked to the above but I attempted to get into the Synaptic Package Manager to see if wine was in there and I got this error: 

> E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I opened a terminal but I cannot run dpkg - - configure -a as I need to be the superuser and when I enter my password for that, I get : -

> su: Authentication failure

Sorry to be a pain but, anybody got any ideas?

---

### Post by Paqman on 2008-06-09
> **timofthec said:**
> 
I downloaded and attempted to run wine ver 0.9.53, however, I get the following error in wubi when I ran the package: -


Well, Wine is in the repos, but it's a slightly later version than that. I'd be inclined to try it anyway, chances are a later version will run your app better.

Btw, are you sure than Open Office Calc isn't going to do the job for you?

If the version of Wine from the repos is no good, then just uninstall it without uninstalling the dependencies and you should be able to install your older version without the dependency error you've been getting.

> 
I opened a terminal but I cannot run dpkg - - configure -a as I need to be the superuser and when I enter my password for that, I get : -

Either you just put your password in wrong, or your system is seriously borked. I'm hoping it's the former.

---

### Post by doorknob60 on 2008-06-09
First of all, are you *sure* you can't use OpenOffice? Also, if you can't get Wine to work, Crossover Office is a great peice of software. I used to use it for Office and it couldn't be easier! It installs with no problems and even sets it so when you double click an office document in nautilus it opens like it should. It costs money, but you can get a free trial and if you buy it, you're supporting Wine :)

---

