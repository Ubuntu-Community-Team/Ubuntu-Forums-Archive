---
title: "Add/Remove Problems"
date: 2007-11-28
forum: General Help
---

### Post by Bigs11 on 2007-11-28
I've installed Ubuntu about 3 or 4 times now, and when I've tried to configure add-ons etc via online linkups, I've had no problems. I'm trying to setup my sound and graphics, add mps drivers and Nvidia support. When I go to Add/Remove and select an app, it says The list of applications is not availabe, and to reload. When I refresh, the same happens. Also when I d/click an Mp3, and try to search for plugins, I get an error. Networking's all set up, and I can use Firefox ok. Have rebooted to no avail.
Any ideas anyone?

---

### Post by scott_g on 2007-11-28
Can you try opening up a terminal (Applications > Accessories > Terminal) and typing:

```

sudo apt-get install <program name>

```

Where <program name> is the name of the program you wish to install.

Then enter your password, and see if there are any errors that show up.

If there are errors, post them please.

Thanks,
Scott

---

### Post by Bigs11 on 2007-11-28
I ran "sudo apt-get install from the terminal and it returned
"reading packages lists...Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded."
So I assume from that, that it's accessing online services properly?

---

### Post by scott_g on 2007-11-28
Try giving it an argument after the install, such as:

```

sudo apt-get install audacity

```

This should install an audio editing program.  If it does, apt-get is working properly, and the problem is elsewhere; if not, the error message should indicate whats going wrong.

EDIT: Could also try:

```

sudo apt-get update

```

Thanks,
Scott

---

### Post by PmDematagoda on 2007-11-28
Could you post the output of:-

```
cat /etc/apt/sources.list
```

---

### Post by Sef on 2007-11-28
> I'm trying to setup my sound and graphics, add mps drivers and Nvidia support. 

Did you change the Add/Remove top right box to 'All Available Applications'?  By doing that you make Universe (GPL nonUbuntu supported applications) and Multiverse (nonGPL [including proprietary] applications) available.

---

### Post by Bigs11 on 2007-11-28
gprice@UbuntuBoy:~$ sudo apt-get install audacity
[sudo] password for gprice:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package audacity

gprice@UbuntuBoy:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_AU
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_AU
Reading package lists... Done

gprice@UbuntuBoy:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
gprice@UbuntuBoy:~$ 

The above list makes me think that I have some sort of restricted version, even though I installed from the same CD I've used the last few times.

---

### Post by scott_g on 2007-11-28
Hmm,  looks like all of your repositories are commented out....

Try going to System > Administration > Software Sources

And check some of the repositories and see if it works....

Thanks,
Scott

---

### Post by PmDematagoda on 2007-11-28
As scott_g said, all your repositories are commented out, you can fix the problem by doing it as the way he suggested. Just remember to reload the sources once you are done, after that is done, try Add/Remove again.

---

### Post by Bigs11 on 2007-11-29
> **scott_g said:**
> Hmm,  looks like all of your repositories are commented out....

Try going to System > Administration > Software Sources

And check some of the repositories and see if it works....

Thanks,
Scott

Pardon the ignorance, but should I turn off some of the Software Sources, and just do trial and error? Just they don't mean too much to me. Won't get back to it till tomorrow anyway, ahd to go to work. :(

---

### Post by PmDematagoda on 2007-11-30
Just enable all the repositories, then try using Add/Remove again.

---

