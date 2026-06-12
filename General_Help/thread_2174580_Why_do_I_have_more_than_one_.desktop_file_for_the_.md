---
title: "Why do I have more than one .desktop file for the Synaptic Package Manager?"
date: 2013-09-15
forum: General Help
---

### Post by vasa1 on 2013-09-15
Posts #1 and #6 in [http://ubuntuforums.org/showthread.php?t=2173769](http://ubuntuforums.org/showthread.php?t=2173769) mention the presence of more than one .desktop file for the Synaptic Package Manager (SPM). I found that I too have two:
```
-rw-r--r--   1 root root   290 May 14 05:47 synaptic.desktop
-rw-r--r--   1 root root   263 May 24 21:36 synaptic-kde.desktop
```
I did a clean install of Lubuntu 13.04 back in April and so the dates for the .desktop files came as a bit of puzzle. I checked /var/log/apt and saw that there was a update of SPM that explains the first entry (synaptic:i386 (0.80~exp2, 0.80~exp2raring1)).
But I can't understand where "synaptic-kde.desktop" came from. I looked at the log for the relevant period (20130514 till 20130531) but don't see any entry that could explain the second file's presence.

---

### Post by ajgreeny on 2013-09-15
That kde desktop file is just one of the default files that is come with synaptic on any system, presumably because synaptic is DE independent.

However, I also note that the kde desktop file is one that opens synaptic without root permissions, using the exec command **synaptic** instead of **synaptic-pkexec**

---

### Post by vasa1 on 2013-09-15
Thanks for clearing that up. In my kde desktop file I see what you mention: just **synaptic** and not **synaptic-pkexec**.

---

