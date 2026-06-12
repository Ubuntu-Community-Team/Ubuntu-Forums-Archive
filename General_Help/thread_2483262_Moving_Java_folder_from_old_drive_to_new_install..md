---
title: "Moving Java folder from old drive to new install."
date: 2023-01-24
forum: General Help
---

### Post by 77_GCSX on 2023-01-24
I have finally upgraded from 16.04 to 22.04. Amazing difference AND TOO easy to do. I do have one question.

I like to play an older version of Minecraft (1.7.2, modded). It really likes and runs well using java-7-openjdk-amd64. Unfortunately I copied the wrong java folder. I have access to the one I need. Can I just copy this folder (and whatever else it may need) to the new install or do I have to actually go through the whole java install process.

Thank You!

---

### Post by TheFu on 2023-01-24
TL;DR answer:
Some programs have loose dependencies and migrate easily.

Other programs are tightly coupled to the libraries used to build them and won't run on systems without those libraries.
JavaRE typically are tightly coupled, even if Java programs strive to be run anywhere.  You'll never know until you try.


Longer explanation:
Libraries (and some programs) usually follow a standard version number scheme.  Let me see if I can find it spelled out at wikipedia.  [https://en.wikipedia.org/wiki/Software_versioning#Schemes](https://en.wikipedia.org/wiki/Software_versioning#Schemes) is the closes.  Basically, if the versions only change in the 3rd level, programs should work except where the 3rd level bug fix breaks it.  Most of the time, updates only to the 3rd level are good.  They aren't supposed to change any API or add any features.

Changes to the 2nd level number are supposed to be additions of new APIs only, which should mean that old programs should work using the old APIs.  Not all projects honor this.

Changes to the 1st level number are major releases and it is common for no backward compatibility to be provided.

At least, that's how the professional teams where I worked did it.  Where I worked, we could run a command to get a list of every module, every library, every 3rd party library version used to build the software from the program directly.  This seems to have fallen out of favor, but many programs commonly used in Linux still provide this if the right tools are run against the programs.  This is something C/C++ programmers have done, but many others do similar.  I don't know what Java does.

A java program/environment from 2016 is over 6 yrs old. It is very unlikely to work on current versions.  What you might consider, to reduce risks, is to setup a Linux Container with just the exact environment and mindcraft, but nothing else. No OS.  Then run that container under the newer release. [https://developers.redhat.com/blog/2019/02/26/create-java-8-runtime-container-image](https://developers.redhat.com/blog/2019/02/26/create-java-8-runtime-container-image) is for Java 8. Might be close enough.  Java7 is long dead with extended support from Oracle ended in 2022.

---

### Post by monkeybrain20122 on 2023-01-24
If it works for java 8 you can get a standalone package here, just extract it and link your program to it (e.g exporting PATH and LD_LIBRARY_PATH when you invoke the program in command line or create a wrapper script and put it in ~/.local/bin) [https://bell-sw.com/pages/downloads/#downloads](https://bell-sw.com/pages/downloads/#downloads)

---

### Post by dragonfly41 on 2023-01-24
You might run ldd in command line to see dependencies of old app.

$ man ldd

---

### Post by 77_GCSX on 2023-01-25
Well, as luck would have it, I was messing around with different Minecraft launchers. I wasn't having any luck UNTIL I downloaded the latest version of Magic Launcher. Inside ML I was again, messing around a I got it!! I don't know exactly how but I get everything working correctly.

For the Java (my version of MC REALLY likes the java-7-openjdk-amd64. Since I had this from my previous install I just moved the folder over to 22.04 and saved it where it should be (the correct directory structure for MC) and pointed my updated ML to is and the game folder and it worked!!

Problem Solved!

Thank You.

---

