---
title: "Gnome / Kde"
date: 2006-12-09
forum: General Help
---

### Post by yojimbosteel on 2006-12-09
What is the difference between GNOME and KDE? I am using Ubuntu Edgy, so I'm using GNOME but apparently I can install KDE programs, for instance I installed Amarok and it worked just fine. So that leaves me wondering... what's the difference. Can I just install KDE programs without any problems?

---

### Post by hikaricore on 2006-12-09
Most KDE applications will run just fine in Gnome, albeit a little slower in some cases.  The difference is just the design and functionality, it pretty much comes down to personal preference.

---

### Post by smoker on 2006-12-09
best way to find out is to try them both and see the differences for yourself, there is some info on the thread below:

[http://www.ubuntuforums.org/showthread.php?t=315630](http://www.ubuntuforums.org/showthread.php?t=315630)

---

### Post by hytek on 2006-12-09
Most of my users use gnome, but they despise nautilus. I am forced to install konqueror as the standard file browser on all my ubuntu machines.

There are certain dependencies when using kde apps under gnome, but installing them by synaptic usually takes care of all of them. <3 synaptic 8)

---

### Post by aysiu on 2006-12-09
There are some disadvantages to running KDE applications in Gnome or Gnome applications in KDE.

1. They look ugly--they don't integrate with your native theme.

2. They require slightly more RAM to be used, since you'll be loading up both KDE libraries and Gnome libraries. But if you have anything over 256 MB of RAM, you should be fine. The applications will also take a little bit longer to load up than native applications (maybe an extra few seconds).

3. In rare cases, the applications may not behave the way you want them to. For example, if you drag and drop a song from AmaroK to your Gnome desktop, it'll **move** the file instead of copying it. If, however, you drag and drop it to your KDE desktop, it'll **copy** the file. One way around this is to open up Konqueror inside Gnome and then drag and drop from AmaroK to Konqueror.

---

### Post by max.diems on 2006-12-09
Also test Xubuntu if you don't have much RAM, and you have more RAM avaliable for KDE libs.

---

### Post by strabes on 2006-12-10
yojimbosteel: gnome and kde are just different desktop environments. you can try out both by running ```
sudo apt-get install kubuntu-desktop
``` then on the login screen, go to sessions, and choose KDE.

---

### Post by sunspots on 2006-12-10
This is interesting to know. As I felt that KDE seemed to have more unique applications than GNOME.

Remember that installing KDE desktop will require about 650-700 megs of disk space.

---

### Post by yojimbosteel on 2006-12-10
I'll have to give it a try and see how I like it :) 
Thanks for the clarifications everyone.

---

