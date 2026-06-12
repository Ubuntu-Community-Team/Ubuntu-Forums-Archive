---
title: "howto: installing a Fiesty package ??"
date: 2007-02-27
forum: General Help
---

### Post by matva on 2007-02-27
hi,

i want to try the latest xine-lib version 1.1.4 as it is supposed to fix audio sync problems.

fiesty is using 1.1.4 so does that mean the package exists? i believe it is called libxine1 (the package name)

i have located it here: [http://packages.ubuntu.com/feisty/libs/libxine1](http://packages.ubuntu.com/feisty/libs/libxine1)

how do i download it and install it to my system? can someone detail it step-by-step for me? do i have to d/l the .deb and install it or can i do apt-get? Thanks

---

### Post by Kateikyoushi on 2007-02-27
I doubt you can apt get it. You could install the deb but it might require you to install a few other packages read it's dependencies and generally it is not recommended. I did it and did not mess up my system could update to feisty.

---

### Post by matva on 2007-02-27
? u installed the deb package for libxine1?

i dont understand why they dont just release the updated libxine1 for current ubuntu since there is a rather huge bug in it (NTSC DVDs play out of sync, ie it is completely useless for NTSC DVD playback).

---

### Post by Kateikyoushi on 2007-02-27
No, not he exact same package. Actually I wanted to install something from debian testing and installed it with the dependant packages about 5 packages and nothing went wrong so far even after upgrading to feisty.

Maybe the package will be backported.

---

### Post by igknighted on 2007-02-27
You *could* (and **I by no means endorse this**, but if you are willing to chance your system go ahead and try it) change you edgy repo's to fiesty (or at least the ones that include libxine).  The apt-get update, apt-get install libxine1, let it do its thing, then change your sources.list back to normal and apt-get update again.  It might work, but if packages have been renamed or if it needs a lot of dependencies, it might be a disaster.

---

### Post by chuckyp on 2007-02-27
That would prompt him to update every other package on the system.  Why doesn't he just download and install the deb from packages.ubuntu.com.  

A tip for you you can dpkg -I nameofdeb.deb to see info on the package prior to installing it.  It will list dependencies etc... Just make sure you meet them all with appropriate versions prior to installing it.   The nice thing about installing via a deb is if you want to remove it you could just dpkg -r nameofdeb.deb when it blows up.

---

### Post by konst88 on 2007-02-27
I would like to try this, but how can i downgrade back to the version from the repositories, if things went wrong?

---

### Post by Ramses de Norre on 2007-02-27
```
sudo aptitude install libxine1/edgy-security
```

---

### Post by konst88 on 2007-02-27
How do you know you it is edgy-security? Or it is always this one?

---

### Post by Ramses de Norre on 2007-02-27
```
apt-cache policy libxine1
```
shows the version table, which states that the newest version is in edgy-security.

> ramses@icarus:~$ apt-cache policy libxine1
libxine1:
  Installed: 1.1.2+repacked1-0ubuntu3.2
  Candidate: 1.1.2+repacked1-0ubuntu3.2
  Version table:
 *** 1.1.2+repacked1-0ubuntu3.2 0
        500 [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Packages
        100 /var/lib/dpkg/status
     1.1.2+repacked1-0ubuntu3 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy/main Packages


---

### Post by konst88 on 2007-02-27
WOW!!
APT is cool!!
Thx!!

---

### Post by Kenno on 2007-03-01
Other than installing the feisty deb, you can also compile Xine 1.1.4 from source, as described [_here_]("http://ubuntuforums.org/showthread.php?p=2112507#post2112507"). It has the advantage that aptitude, synaptic and update-manager won't complain about things being broken, but apart from that, it's equally bad for your system at best. Luckily, it hasn't caused me any problems so far.

---

### Post by Kenno on 2007-03-09
Look what fell into the update-box today.
> 
libxine1
From version 1.1.2+repacked1-0ubuntu3.2 to 1.1.2+repacked1-0ubuntu3.3

The only explanation I have is that they're not planning to include 1.1.4 in Edgy at all. Guess people who like movies and don't want to risk messing up their system have to wait 6 more weeks.
> Feisty Fawn is going to be the next Ubuntu release, currently scheduled for release on 19 April 2007.

---

