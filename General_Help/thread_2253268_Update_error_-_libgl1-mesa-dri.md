---
title: "Update error - libgl1-mesa-dri"
date: 2014-11-18
forum: General Help
---

### Post by schnor77 on 2014-11-18
Hi all,

Long-time lurker, first time poster!

Just checking I'm correct before I continue (Ubuntu 12.04.5 LTS). I   checked for updates - via update manager - this morning and found 13   updates to OPENGL & GL drivers, etc relating to : -

```
mesa (10.1.3-0ubuntu0.2) trusty; urgency=medium

  [ Timo Aaltonen ]
  * Drop fix-kwin.diff hack, as 10.1.3 has 0380ec467d78f40 which
    fixes the issue properly.

  [ Maarten Lankhorst ]
  * Add fix-svga-ioctl.patch (LP: [#1365490]("https://bugs.launchpad.net/ubuntu/+source/mesa-lts-trusty/+bug/1365490") bug 1365490
```

Half way through installing it returns a broken package system: -

```
The following packages have unmet dependencies:

libgl1-mesa-dri-lts-trusty: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
libgl1-mesa-dri-lts-trusty:i386: Depends: libgcc1 (>= 1:4.1.1) but 1:4.6.3-1ubuntu5 is installed
```

apt-get install -f didn't work as 

```
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

I then tried to fix the *Error: Broken count <0* (as TBH the solutions I've found to opening the locked file is a bit much for me): -

```
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

Which gave me: -

```
dpkg: error processing libgl1-mesa-dri-lts-trusty (--configure):
 libgl1-mesa-dri-lts-trusty:amd64 10.1.3-0ubuntu0.2~precise1 cannot be configured because libgl1-mesa-dri-lts-trusty:i386 is in a different version (10.1.3-0ubuntu0.1~precise1)
dpkg: error processing libgl1-mesa-dri-lts-trusty:i386 (--configure):
 libgl1-mesa-dri-lts-trusty:i386 10.1.3-0ubuntu0.1~precise1 cannot be configured because libgl1-mesa-dri-lts-trusty:amd64 is in a different version (10.1.3-0ubuntu0.2~precise1)
Errors were encountered while processing:
 libgl1-mesa-dri-lts-trusty
 libgl1-mesa-dri-lts-trusty:i386
```

Is the issue that it's trying to install a trusty package on a precise machine? Would it be a patch / distribution issue? If so I'll *sudo apt-get update* in 24/48 hours. I'd rather this than trying a fix.

Speaking of a fix, in my searches I found [[URL=&quot;https://ubuntuforums.org/showthread.php?t=1940733[/URL"]this thread]("https://ubuntuforums.org/showthread.php?t=1940733)

Am I safe to *gulp* purge my driver(s)?

```
dpkg --force-depends --purge libgl1-mesa-dri
sudo apt-get -f install
```

Many thanks in advance :grin:

---

### Post by schnor77 on 2014-11-19
Just a cheeky bump for the evening crowd. 

I'll give it 24 hours then try a driver purge. Will update the thread if it works / doesn't work in case anyone else has this problem :)

---

### Post by Bashing-om on 2014-11-19
schnor77; Hello;

I agree, looks to be a graphics driver issue.
Did you, at some time resort to the  "Intel Graphics driver installer" such that now that newer driver is broke, when the system files were updated  ?

I am not Intel savvy, may have to await others to advise better as to how to remove/install the Intel graphics driver for the HWE (HardWare Enablement stack) enhanced kernel.

[INDENT][INDENT]not much, but a start
[/INDENT][/INDENT]

---

### Post by schnor77 on 2014-11-19
Hi Bashing-om,

Thanks for the info! No, I didn't touch the drivers - just went about my daily update. As you said, maybe someone more Intel savvy will come along and advise :)

---

### Post by schnor77 on 2014-11-20
Well that was easier than I thought - took 30 secs :)

```
sudo dpkg --force-depends --purge libgl1-mesa-dri-lts-trusty:i386
sudo apt-get -f install
sudo apt-get update
```

---

### Post by Bashing-om on 2014-11-20
schnor77; Hey;

You done good !

If no one else came up with better, I was going to suggest (RE-)installing all the packages related to the HardWare Enablement stack ( amongst what you did, so all of it would have been overkill).

As all is now good:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]just keep on keep'n on
[/INDENT][/INDENT]

---

### Post by schnor77 on 2014-11-21
Thanks for the reminder - thread solved!

---

