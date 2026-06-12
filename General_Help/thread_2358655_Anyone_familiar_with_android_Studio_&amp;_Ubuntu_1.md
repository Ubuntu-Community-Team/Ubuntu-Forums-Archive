---
title: "Anyone familiar with android Studio &amp; Ubuntu 16.04?"
date: 2017-04-15
forum: General Help
---

### Post by garyed on 2017-04-15
Is there some kind of path that needs to be set in order to get the android emulator to work? I have Android studio installed & working but the emulator doesn't work. It used to work before i upgraded from 14.04 to 16.04 & I can't remember what i had to do to get it working before. 
Any help appreciated.

---

### Post by garyed on 2017-04-17
Bumpity Bump..

Does anyone know of a forum where I might can get some help?

---

### Post by wildmanne39 on 2017-04-17
You can look at this link it might help:
[https://stackoverflow.com/questions/35911302/cannot-launch-emulator-on-linux-ubuntu-15-10](https://stackoverflow.com/questions/35911302/cannot-launch-emulator-on-linux-ubuntu-15-10)

---

### Post by garyed on 2017-04-17
Thanks but i couldn't make things work. It's been very frustrating trying to get Android Studio emulator to work in Ubuntu 16.04. I wish I could remember what I did to get it working in 14.04 but I just can't. I did a clean install of 16.04 just to get it working & I still have the same problem.

---

### Post by wildmanne39 on 2017-04-17
I am sorry, I have never used this before or attempted too.

Best of luck.

---

### Post by garyed on 2017-04-21
Actually the very last line on that link did work on one of my versions of Ubuntu Studio 16.04 & the plain Ununtu 16.04 all i had to do was delete all the libstdc++* files in Android studio.  

This was the one that i used from stack Overflow but the directory where my libstdc++ files were different in Andriod Studio:
> Verify that you have installed in your system lib64stdc++6

With a 32 bits operating system :

# apt-get install lib64stdc++6
With a 64 bits operating system with multiarch enabled :

# apt-get install lib64stdc++6:i386
Then link the new installed libraries to the android sdk tools path

$ cd $ANDROID_HOME/android-sdk-linux_x86/tools/lib64/libstdc++
$ mv libstdc++.so.6 libstdc++.so.6.bak
$ ln -s /usr/lib64/libstdc++.so.6 $ANDROID_HOME/android-sdk-linux_x86/tools/lib64/libstdc++ 
Thanks again for pointing me in the right direction

---

### Post by nptroom on 2017-05-03
im nob using android studio on ubuntu all its instaled, im just watching tutorial on youtube the tutorial about connecting php to android studio but on the video one step using notepad to make a script and i dont no how to do it on ubuntu any one know thanks and sorry for bad english

---

### Post by garyed on 2017-05-03
I didn't think php was of any use with android studio. I have converted mysql databases that I use with php to sqlite3 for use in android studio but that's about it. I'm pretty much a novice too so I don't know much about that stuff.

---

