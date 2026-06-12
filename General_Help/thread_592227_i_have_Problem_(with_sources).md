---
title: "i have Problem (with sources)"
date: 2007-10-26
forum: General Help
---

### Post by Smart_Hacker on 2007-10-26
[CENTER][B]i have proplem in update
i think it in sources file 
i have UBUNTU 7.10 GUTSY DVD COPY
what i can do?!
Please Help Me:([/B][/CENTER]

---

### Post by PmDematagoda on 2007-10-26
Could you please make your question more specific? I only got two parts, you think you have a broken sources.list file and that you have a Gutsy DVD, yet I do not see the connection.

---

### Post by Smart_Hacker on 2007-10-26
yeah my sources.list file broken 
what i can do?!
coz my UbunU not updateing the packge

---

### Post by PmDematagoda on 2007-10-26
Ok, could you please post your sources.list file using:-

```
gedit /etc/apt/sources.list
```

---

### Post by Smart_Hacker on 2007-10-26
this my soures.list
```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071017)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://il.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://il.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://il.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://il.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://il.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://il.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

---

### Post by PmDematagoda on 2007-10-26
Open up Software Sources in System>Software Sources and enable all the choices in the Ubuntu Software tab, and enable all the choices except the "Proposed Updates" in the Updates tab and see if you can update/upgrade Ubuntu.

---

### Post by Smart_Hacker on 2007-10-26
Thank u i will try it now

---

### Post by Smart_Hacker on 2007-10-26
[SIZE="4"]enable this :[/SIZE]

[IMG]http://www.m5zzn.com/uploads/69376684c7.png[/IMG]

[SIZE="4"]or This[/SIZE]

[IMG]http://www.m5zzn.com/uploads/7486998c5d.png[/IMG]
[SIZE="4"]
or This[/SIZE]

[IMG]http://www.m5zzn.com/uploads/d2a8f793f3.png[/IMG]

---

### Post by PmDematagoda on 2007-10-26
Activate all the choices in the first screenshot. Activate all the choices in the third screenshot except the "Pre-Released Updates". The second screenshot is not that important for now.

---

### Post by Smart_Hacker on 2007-10-26
[IMG]http://www.m5zzn.com/uploads/b72f4efaeb.png[/IMG]

:confused::confused::confused::(:(:(:(

---

### Post by PmDematagoda on 2007-10-26
Very well, try changing the server location and see if that solves your problem. 

If that doesn't work then disable the Unsupported-updates as well in the 3rd screenshot and see if that works.

---

### Post by Smart_Hacker on 2007-10-26
thank u very much but what ur best server?!

---

### Post by PmDematagoda on 2007-10-26
I currently use the Sri Lankan server and it works just fine, you could try the closest server that you have other than the one currently being used.

---

### Post by Smart_Hacker on 2007-10-26
thank u
bu some servers have not all package:(

---

### Post by PmDematagoda on 2007-10-26
Then give the US server a try.

---

### Post by Smart_Hacker on 2007-10-26
thank u
i will try:evil:

---

### Post by Smart_Hacker on 2007-10-26
please i wanna a server have all package please help me
:(:(:(

---

### Post by Smart_Hacker on 2007-10-26
^^
<<up>>

---

