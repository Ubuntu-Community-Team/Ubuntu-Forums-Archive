---
title: "32 bit libraries for Kubuntu 17.10"
date: 2017-11-22
forum: General Help
---

### Post by YuiDaoren on 2017-11-22
How do I get 32 bit libraries/support installed in 64 bit Kubuntu 17.10? I've had no success with the methods suggested for earlier versions.

---

### Post by #&amp;thj^% on 2017-11-22
Can You tell us what you have Tried then?
So we are not wasting your and our time here Repeating.
Edit: So I guess you have done this then?
```
sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 lib32z1
```

---

### Post by YuiDaoren on 2017-11-22
I apologise, I know better than to be so vague.

what I had tried was:
```
sudo apt-get install ia32-libs ia32-libs-gtk ia32-libs-kde ia32-libs-sdl
```

which said no such packages.


Thank you for your answer! Did as you posted, and successfully installed, but...

the program (Second Life viewer) still did not launch.

BUT this time I was able to sus out the library in question and an additional
```
sudo apt install libgtk2.0-0:i386
```
got me going.

Again, thanks!

---

