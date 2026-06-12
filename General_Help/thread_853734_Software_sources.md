---
title: "Software sources"
date: 2008-07-08
forum: General Help
---

### Post by planet-reptile on 2008-07-08
Hi.

In software sources under updates I cannot check the top box where it says "important security updates" (Hardy security) 
[IMG]http://i287.photobucket.com/albums/ll131/planet-reptile/Diverse/Skrmbillede-3.png[/IMG]

But under Third-party software it looks like hardy security is marked. Does it mean i don't have to worry about not getting security updates?
[IMG]http://i287.photobucket.com/albums/ll131/planet-reptile/Diverse/Skrmbillede-1-2.png[/IMG]

---

### Post by iaculallad on 2008-07-08
Post whatever displays when you issue the command below:

```
cat /etc/apt/sources.list
```

---

### Post by planet-reptile on 2008-07-09
Hi. 

This is how it looks.

kim@kim-desktop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) hardy-proposed restricted main multiverse universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
kim@kim-desktop:~$

---

### Post by drs305 on 2008-07-09
> **planet-reptile said:**
> Hi.

In software sources under updates I cannot check the top box where it says "important security updates" (Hardy security) 
[IMG]http://i287.photobucket.com/albums/ll131/planet-reptile/Diverse/Skrmbillede-3.png[/IMG]

But under Third-party software it looks like hardy security is marked. Does it mean i don't have to worry about not getting security updates?
[IMG]http://i287.photobucket.com/albums/ll131/planet-reptile/Diverse/Skrmbillede-1-2.png[/IMG]

Your sources.list includes the security updates, so you should be protected. When you check (or uncheck) the security box in "Updates" the sources list is modified and updated.

---

### Post by planet-reptile on 2008-07-09
> Your sources.list includes the security updates, so you should be protected. When you check (or uncheck) the security box in "Updates" the sources list is modified and updated. 
But i can't check the security box in updates. There is no mark in the box when i try to check it. But in third-party software the hardy security is there and is marked. So do i need to worry about not getting security updates?

---

### Post by drs305 on 2008-07-09
> **planet-reptile said:**
> But i can't check the security box in updates. There is no mark in the box when i try to check it. But in third-party software the hardy security is there and is marked. So do i need to worry about not getting security updates?

The answer is you are protected although I am not sure why you can't select the security tick box in Updates. If you look at what ticking that box does, it includes the following line in sources.list:
```
deb http://security.ubuntu.com/ubuntu/ hardy-security restricted main multiverse universe

```

You can see hardy-security restricted, main, multiverse and universe - all of which are in your sources.list.  So yes, you are going to get those updates when you run "sudo apt-get update && sudo apt-get upgrade" or are notified via update manager. 

As to why you can't check the Update security box I will have to investigate but don't have an answer.

---

### Post by drs305 on 2008-07-09
Update: There has been a bug report on this issue.

Here is the recommended fix:
```
Temporary fix:
1) sudo sed -e 's/security\.ubuntu\.com/archive\.ubuntu\.com/g' /etc/apt/sources.list > /etc/apt/sources.list.tmp
sudo mv /etc/apt/sources.list.tmp /etc/apt/sources.list
sudo apt-get update

2) Don't uncheck/check the hardy-security in Software Sources until it's fixed.
```


Here is the bug report:
[https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093]("https://bugs.edge.launchpad.net/ubuntu/+source/software-properties/+bug/244093")

Note: There are other possible remedies in the remarks section in addition to the above suggestion.

---

### Post by planet-reptile on 2008-07-11
The fix does not work.

---

### Post by drs305 on 2008-07-11
> **planet-reptile said:**
> The fix does not work.

The comments section of the bug report had several solutions. The last one I saw posted (18 hours ago) by Savvas had a solution which included downloading the file "Ubuntu.info". Did you try that one?

Since I'm not having the problem I don't know if it would fix things or not.

Good luck.

---

### Post by planet-reptile on 2008-07-11
I found the solution in the bug thread.
If any of you should have the same problem as I do the following and all is back to normal.

Execute in terminal: gksu gedit /etc/apt/sources.list

Change any occurence security.ubuntu.com to archive.ubuntu.com

For example, I changed:
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

..to:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-security universe main multiverse restricted

..things will be back to normal:

(I have copypasted the solution so that people here can see the solution)

This is how it looks now:

[IMG]http://i287.photobucket.com/albums/ll131/planet-reptile/Diverse/Skrmbillede-4.png[/IMG]

[IMG]http://i287.photobucket.com/albums/ll131/planet-reptile/Diverse/Skrmbillede-1-3.png[/IMG]

---

