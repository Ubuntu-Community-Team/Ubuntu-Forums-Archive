---
title: "Ubuntu partitions configuration and speed up."
date: 2013-02-16
forum: General Help
---

### Post by x6itru on 2013-02-16
Hello there. Today, i decided to switch to Ubuntu(12.10 x64). I will be using it to games programming ( C++ & OpenGL ). I need help in configuration, i already had ubuntu (3month ago?), but it doesn't work faster than windows ( unfortunetly slower ), so i switch to Windows again :( . For desktop environment i have chosen gnome shell. 

PC Config :
AMD Phenom II 4x B55 3.20GHZ
ATI Radeon HD4870 1GB << a little problem with drivers on 12.10
RAM 6GB
HD 500GB

Now the questions.
1. How to split hard-drive(How much space for each partition(swap etc.)
2. How to optimize it, i need it as smooth as windows7 :/

Regards. x6itru!

---

### Post by dino99 on 2013-02-16
here is my standard choice:

[http://ubuntuforums.org/showpost.php?p=12495221&postcount=2](http://ubuntuforums.org/showpost.php?p=12495221&postcount=2)

as your needs may vary from mine, your swap could be widen depending of how many libs/apps/screens are loaded/opened at once while coding etc

---

### Post by Mark Phelps on 2013-02-16
> **x6itru said:**
> ATI Radeon HD4870 1GB << a little problem with drivers on 12.10
There are NO restricted AMD drivers that will work with that video chipset and Ubuntu versions newer than 12.04 because 12.10 brings a new X-server version and AMD is not going to update the HD 2x/3x/4x series chipsets to work with that X-server.  So, the open-source drivers are what you are stuck with in 12.10 and newer.

> 2. How to optimize it, i need it as smooth as windows7 :/
Basically, not possible -- why? Because Win7 has optimized video drivers that work with your video chipset and, as already mentioned, Ubuntu 12.10 does not.

Also, modern games generally need hardware acceleration to get decent frame rates and you will not get that with Ubuntu 12.10.

So, if Gaming is your focus, you would do best to use nothing newer than 12.04.

---

### Post by x6itru on 2013-02-16
[https://launchpad.net/~makson96/+archive/fglrx](https://launchpad.net/~makson96/+archive/fglrx) << its working very well, but i will test 12.04 too maybe it will be faster?

BTW, on this drivers + 12.10 x64 , in glxgears im getting 7k fps~ i will try 12.04 too

---

### Post by x6itru on 2013-02-17
i've just tested 12.04, and it seems to be worst than 12.10, I cant install ANY ati drivers *.* Every attemp destroying my ubuntu. :O


@@@@EDIT
I've just check my XORG version in 12.04,
And i saw 1.13.0 WTF is that? ;___: ATI drivers work only with XORG 1.12 :/ AFF, btw theres the same on Fedora 18/17 so its no matter which distribution i will choose ;/ i dont know what should i do now ;(

---

### Post by Mark Phelps on 2013-02-17
Unfortunately, given that AMD has dropped support for the "older" chipsets, you're basically (like me) at a dead end.  You will need to run an X-server no newer than 12.1 -- which rules out any Ubuntu version newer than 12.04.

The only other alternative (if it's even possible for you) is to upgrade to a AMD chipset that is supported -- HD 5x or newer.

---

