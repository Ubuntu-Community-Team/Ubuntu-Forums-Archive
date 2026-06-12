---
title: "libavcodec54 (on Saucy): Problem with weird dependency chain"
date: 2013-11-19
forum: General Help
---

### Post by syntaxerror74 on 2013-11-19
I'm on Saucy and AFAICS I cannot do without libavcodec54 if I want to rip audio from video...
However, somehow the dependency chain got broken in Saucy: packages depend on other packages whose versions are not available in current stable (otherwise they would have been shown in aptitude, huh?)
And although I'm pretty experienced with dependencies *when installing everything manually via dpkg*, there is still something to learn for me with that aptitude method: (read: no kludges, no ugly DIY hackery!)

```
$ sudo apt-get install libavcodec54
Reading package lists... Done
Building dependency tree       
<snip>
The following packages have unmet dependencies.
 libavcodec54 : Depends: libopus0 (>= 1.1~beta) but 1.0.1-0ubuntu2 is to be installed
                Depends: libva1 (> 1.2.0~) but 1.1.1-3 is to be installed
E: Unable to correct problems, you have held broken packages
```

I could easily solve this problem myself by tricking around with Debian packages (i. e. those meant for *genuine* Debian) but actually I'd like to solve it without doing such "inofficial" kludges.

Is there only the way out to take packages from unstable, i. e. Trusty Tahr PPA? I don't want to believe that.
On the other hand, it would also have worked if aptitude did NOT offer the very latest package whose dependencies cannot be met in current stable, but one version before. It even looks as if the "balance" got lost in Saucy, since everything went perfectly so far and I never had that dependency fight before the requirement of libavcodec54.

---

