---
title: "Questions from a new ubuntu user"
date: 2004-11-15
forum: General Help
---

### Post by Rabbit on 2004-11-15
I'm currently running SuSE 9.1 which I got from Novell as eval edition (long story) anyways, I installed it, it looked great worked as promise but there was little things about it just drove me crazy. (First being KDE) Ubuntu Linux is a name I keep hearing again and again from some friends. I have a few questions though. 

1. I dualboot with Windows. I assume ubuntu will support that during the install. (Yes, I use firefox, Thunderbird, Sunbird and Xchat in Windows)

2. I have Nvidia Geforce 5200 Ultra. It's a dual headed card with 2 monitors hooked up to it. I really like to have that in Linux. I was told to edit my X86Config to support that and I ended up frying X something good. I also forgot to make a backup copy of it and it never worked the same again. Does Ubuntu support Nvidia and such or am I going Vi in random config files till I can get something to work or blow it up? (which ever comes first)

3. How much development tools does it come with? That's what I hated about SuSE. It seemed everytime I was trying to compile something, some development package wasn't there. It drove me crazy. I ended up in dependence hell (like DLL hell) and SuSE was about year behind the rest of the modern world. I didn't even ship with Firefox....(mozilla 1.4 or something was on there)

---

### Post by ynef on 2004-11-15
1 -- Yup, the install will detect Windows and configure the boot loader for you.

2 -- Installing the nvidia driver requires some work, but it's all very well outlined in [this guide](http://wiki.ubuntu.com/BinaryDriverHowto). To get two displays up and running, you do as you'd do in any distro -- editing your X config file. I don't have two displays, but the NVIDIA readme has a section on this, I think.

3 -- Ubuntu doesn't come with a lot of development tools, since it's a desktop distribution and not really geared towards programmers. **However**, you can easily install packages from the debian repositories (actually, you get them from the ubuntu server and they're in the repos "universe" and "metaverse") which means you get full access to virtually all development tools made for Linux.

---

### Post by Juergen on 2004-11-15
[QUOTE=Rabbit]3. How much development tools does it come with? That's what I hated about SuSE. It seemed everytime I was trying to compile something, some development package wasn't there.[/QUOTE]
I wouldn't count the lib-devel-packages to the development-**tools** , but anyway

the packages are devided into blah and blah-devel, like in SuSE, so if you want to compile stuff yourself you'll probably have to install lots of those *-devel packages first.

But there are tools to help you:
'apt-get build-dep' should try to satisfy the dependencies, if you have a source-package for your proggie.

If you compile from *.tgz, try autoapt. This monitors the file access of programs under it's control and if files are accessed  (tried to, that is) that are in uninstalled packages it automatically downloads and installs these packages before it lets the operation continue.
So you would do 'auto-apt ./configure' etc.

But let me tell you: I haven't used either of these tools - with >14000 packages available I didn't have to compile something so far...  :grin:

---

