---
title: "apt-get autoremove wiped out desktop"
date: 2007-03-06
forum: General Help
---

### Post by tyler_roach on 2007-03-06
A very strange thing happened to me today:

Recently, "apt-get" started giving me a huge list of packages that "are no longer needed and can be removed." This was an annoyance, as this long list popped up every time i used apt-get or aptitude. So this morning I did the "apt-get autoremove" like it told me, and lo and behold, KDE is completely uninstalled! I got it back with "aptitude install kubuntu-desktop" so everything is fine now (I hope), but my question is: What the hell happened? I thought autoremove only deleted superfluous .deb files in the cache, not that it uninstalled anything! What exactly does it do? Is there any way to prevent it from giving me that long of packages that "are no longer needed and can be removed," when these packages are DESPERATELY needed and cannot be removed? 

Also,  is there any way to find out which packages were removed? I'm afraid I may have uninstalled things I don't know about and may need.

Thanks.

---

### Post by kidders on 2007-03-06
Hi there,

You may be confusing "autoremove" with "autoclean". Afaik, **apt-get autoremove** will uninstall applications that, in dependency terms, have no reason for being on your system. It's not a wise thing to do without good reason.

> Also, is there any way to find out which packages were removed? I'm afraid I may have uninstalled things I don't know about and may need.Check your system logs. You should be able to figure out a list of what's been uninstalled.

---

### Post by yabbadabbadont on 2007-03-06
You probably removed some small program that you didn't want (or need), but which is listed as a dependency of kubuntu-desktop.  It probably told you that it would remove kubuntu-desktop when you removed it and you removed it anyway.  No problem.  Except that kubuntu-desktop was directly responsible for pulling in a ton of packages when the system was installed.  Now that it is gone, all those packages are marked for autoremoval because kubuntu-desktop was the only thing that depended on them.  Then you used the autoremove option...  :D

---

### Post by tyler_roach on 2007-03-07
> **yabbadabbadont said:**
> You probably removed some small program that you didn't want (or need), but which is listed as a dependency of kubuntu-desktop.  It probably told you that it would remove kubuntu-desktop when you removed it and you removed it anyway.  No problem.  Except that kubuntu-desktop was directly responsible for pulling in a ton of packages when the system was installed.  Now that it is gone, all those packages are marked for autoremoval because kubuntu-desktop was the only thing that depended on them.  Then you used the autoremove option...  :D

Yes, that's exactly what happened... And I did confuse auto remove with autoclean.

I think someone should come up with a fix for this issue... The packages that are install with major, important metapackages like kubuntu-desktop and ubuntu-desktop shouldn't be marked for autoremoval when the metapackage is removed, or better yet, the metapackage shouldn't be removed when one of its dependencies is. It's very annoying to get a list of a hundred "to be removed' packages" every time you use apt.

There was another thread here today about a similar issue.:
[http://www.ubuntuforums.org/showthread.php?t=378140](http://www.ubuntuforums.org/showthread.php?t=378140)

---

### Post by kidders on 2007-03-07
> **tyler_roach said:**
> The packages that are install with major, important metapackages like kubuntu-desktop and ubuntu-desktop shouldn't be marked for autoremoval when the metapackage is removed, or better yet, the metapackage shouldn't be removed when one of its dependencies is.This seems like a strange thing to _*want*_ to have happen.

If your package manager claims that obviously important applications really ought to be removed, that suggests you may have done something in the past that had an impact you didn't anticipate. The best advice is to take care when removing applications ... especially ones you didn't actually install by name.

**Edit:** I just realised that last comment was a bit cryptic! What I mean is that, if you install an application by actually typing its name (eg **apt-get install openssh-server**), and the package manager pulls in 10 other applications, uninstalling any of those dependencies is not necessarily a good idea.

---

### Post by bitnix on 2007-10-28
I have had the same problem, autoremove tells me to remove a lot of package... I also find another old post about the bug
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/75882](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/75882)

hope to be helpful...

---

### Post by Wiebelhaus on 2007-10-28
Random Comment of the day.


I dated a girl in high school by the last name of Roach , She was a fire cracker , hotter than Madonna's panties , God I wish I kept in touch with her.

---

### Post by skralljt on 2008-01-19
This problem just got me, apt-get suggested that I do an apt-get autoremove for what looked like lots of unimportant programs.  Unfortunately, I missed mysql in there, and it wiped out my flipping amarok database support.  I hope that the amarok database is still in there somewhere, i don't look forward to teaching the damn thing what kind of music I want to listen to again...

---

