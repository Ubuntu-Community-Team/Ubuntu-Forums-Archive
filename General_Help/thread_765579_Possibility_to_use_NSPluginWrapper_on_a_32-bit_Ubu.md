---
title: "Possibility to use NSPluginWrapper on a 32-bit Ubuntu Install"
date: 2008-04-24
forum: General Help
---

### Post by yaknowwat on 2008-04-24
Was wondering if it was possible to install and use NSPluginWrapper on a 32 bit Ubuntu linux in order to wrap flash player as flash crashes a lot when PulseAudio is installed and used.  PulseAudio by default is in 8.04 too. I understand NSPluginWrapper won't completely solve the problem but it will stop browser crashes when flash crashes at least.

---

### Post by yaknowwat on 2008-04-24
bump just wondering because more than i will have this problem.

---

### Post by psyke83 on 2008-04-24
Yes, I uploaded nspluginwrapper built for i386 a couple of days ago. You can get it on bug [192888]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/192888"), comment 39. Remember to also install libflashsupport, and you definitely need to perform a reinstall of flashplugin-nonfree *after* you install nspluginwrapper.

```
$ sudo apt-get install flashplugin-nonfree --reinstall
```

If you have success, please add a comment to the bug report and state your basic system specs, your experience with flash before installing nspluginwrapper (e.g. if flash could share audio with other applications or not), and your experience afterwards.

---

### Post by yaknowwat on 2008-04-24
Thank you works nicely now.

Also i commented and posted a lshw output log. (as an attachment because it was kind of big)
and what i did.

---

