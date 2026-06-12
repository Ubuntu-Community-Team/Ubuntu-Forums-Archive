---
title: "[SOLVED] Add/Remove Application problem"
date: 2007-12-01
forum: General Help
---

### Post by nomemory on 2007-12-01
Hello,
I have a problem with "Add/Remove Applications."
For example I want to install 7zip. I check the program in the list and then I get this message:

> "The list of applications is not available
Click on 'Reload' to load it. To reload the list you need a working internet connection."
(No 'Reload' ?! just 'Refresh' anyway...)

I perform 'Refresh', I check again 7zip, and the same message appears: 
> "The list of applications is not available
Click on 'Reload' to load it. To reload the list you need a working internet connection." (again and again).

Do you have any ideas why ?
Note: I am newbie.

Thank you,

---

### Post by -grubby on 2007-12-01
why not try using synaptic? under system>administration>synaptic

---

### Post by nomemory on 2007-12-01
I will use Synaptic (System/Administration), but i am a little confused why isn't 'Add Remove" working...
PS: nice tutorial site in your signature.

---

### Post by bail_w on 2007-12-01
I just installed Ubutu 7.10, and i am getting the same error, any help ?

---

### Post by nomemory on 2007-12-02
The Add/Remove is still not working.
On the other hand Synaptic is working perfectly (still is not as "user friendly" as Add/Remove). 
 
Do you have any ideas what the problem is ?
Thank, you

---

### Post by PmDematagoda on 2007-12-02
Post the result of:-
```

cat /etc/apt/sources.list
```

---

### Post by nomemory on 2007-12-02
> andrei@andrei-desktop:~$ cat /etc/apt/sources.lisResult:

> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ro.archive.ubuntu.com/ubuntu/](http://ro.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
andrei@andrei-desktop:~$ 



---

### Post by PmDematagoda on 2007-12-02
Open the sources.list file for editing using:-
```

sudo gedit /etc/apt/sources.list
```

And remove the # in front of all the lines such as these:-
```

# deb http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

# deb-src http://ro.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```

After that is done save the file and do:-
```

sudo apt-get update
```

Then see if Add/Remove works properly.

---

### Post by nomemory on 2007-12-02
Yes, It's working now. 
Thank you very much.

But, can you please explain me what was the problem ?
This is my 3rd linux day and I want to understand my actions.

---

### Post by PmDematagoda on 2007-12-02
The repositories that contained the software were disabled, only the essential ones were active, this meant that Synaptic works but does not contain all the software packages found usually on a normal Ubuntu installation, this also caused the Add/Remove malfunction.

And you are welcome:), just mark this thread as solved so that it could benefit other people with your same problem.

---

### Post by nomemory on 2007-12-02
I googled about repositories and I found some explanations about them. I now understand the problem. 

# -> comment 

Solved.
Thanks again.

---

### Post by PhrozenPhoenix on 2007-12-27
Just as a side note, I think the reason you came across this issue was because you didnt have an internet connection established while you were installing Xubuntu... thats probably why the installer commented out all of those repositories.

I just had the same problem and the solution worked perfectly, thanks Dematagota!

---

