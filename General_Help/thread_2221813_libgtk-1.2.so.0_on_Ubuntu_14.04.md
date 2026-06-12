---
title: "libgtk-1.2.so.0 on Ubuntu 14.04"
date: 2014-05-03
forum: General Help
---

### Post by Cory_Mittleider on 2014-05-03
I'm having trouble trying to install a fairly old version of ProEngineer 3D modeling software.  
Here is the error I get when I try to run the installed program:
```
/usr/local/ptc/proeWildfire3.0/i486_linux/obj/MOZILLA/ptc_gecko_server: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
```

I am running Ubuntu 14.04 -64 bit on my Acer 5532.  I've had this software for several years now and have had it installed on several versions of Ubuntu.  It is a 32 bit software, but in the past I've found it has the following dependencies:
*ia32-libs* used before on earlier versions of Ubuntu -now using libsdl1.2debian:i386 for 14.04
*gcc-3.3-base   -saved package installed manually*
*libstdc++5_3.3.6   **-saved package installed manually*
*libmotif3_2.2.3-4    *[I]-saved package installed manually
[/I]
Can someone help me figure out how to install libgtk1.2 or can I point this software to libtgk3.0 somehow?

---

### Post by monkeybrain20122 on 2014-05-03
libgtk-1.2 has been deprecated since Ubuntu 10.04 if not before. The only place I can still find it is [https://launchpad.net/~mati75/+archive/lubuntu-testing/+packages](https://launchpad.net/~mati75/+archive/lubuntu-testing/+packages)
But don't add the ppa since the libgtk-1.2 packages are only for Precise. So you would have to download the .debs from its archive.

According to this thread you need three packages [http://askubuntu.com/questions/181295/basiliskii-in12-04/254162#254162](http://askubuntu.com/questions/181295/basiliskii-in12-04/254162#254162)
The url is of course not valid so you have to get them from the ppa's archive above.

Not sure if you can install them though.

---

### Post by Cory_Mittleider on 2014-05-03
Thanks so much for your quick response.  I think I'm close.  

I've downloaded these 3 files.
```

-rw-rw-r-- 1 cory cory  92404 May  3 22:26 libglib1.2ldbl_1.2.10-20~precise1_i386.deb-rw-rw-r-- 1 cory cory 936696 May  3 22:25 libgtk1.2_1.2.10-18.1build2~precise1_i386.deb
-rw-rw-r-- 1 cory cory 210498 May  3 22:26 libgtk1.2-common_1.2.10-18.1build2~precise1_all.deb

```

When I run "[FONT=Ubuntu Mono]sudo dpkg -i *.deb[/FONT]" I get the following error:
```

cory@cory-laptop:~/Desktop/libgtk1.2$ sudo dpkg -i *.deb(Reading database ... 198117 files and directories currently installed.)
Preparing to unpack libglib1.2ldbl_1.2.10-20~precise1_i386.deb ...
Unpacking libglib1.2ldbl (1.2.10-20~precise1) over (1.2.10-19build1) ...
Selecting previously unselected package libgtk1.2.
Preparing to unpack libgtk1.2_1.2.10-18.1build2~precise1_i386.deb ...
Unpacking libgtk1.2 (1.2.10-18.1build2~precise1) ...
dpkg: warning: downgrading libgtk1.2-common from 1.2.10-18.1build2 to 1.2.10-18.1build2~precise1
Preparing to unpack libgtk1.2-common_1.2.10-18.1build2~precise1_all.deb ...
Unpacking libgtk1.2-common (1.2.10-18.1build2~precise1) over (1.2.10-18.1build2) ...
Setting up libglib1.2ldbl (1.2.10-20~precise1) ...
dpkg: dependency problems prevent configuration of libgtk1.2:
 libgtk1.2 depends on libgtk1.2-common (>= 1.2.10-18.1build2~precise1).


dpkg: error processing package libgtk1.2 (--install):
 dependency problems - leaving unconfigured
Setting up libgtk1.2-common (1.2.10-18.1build2~precise1) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...
Errors were encountered while processing:
 libgtk1.2

```

Any idea how to resolve this error?

---

### Post by monkeybrain20122 on 2014-05-04
> dpkg: warning: downgrading libgtk1.2-common from 1.2.10-18.1build2 to 1.2.10-18.1build2~precise1

How come? it looks like you already somehow have libgtk1.2-common installed. How did you install it? I am not on 14.04 right now but unless they have brought it back I don't think it is even in the repo (not in 13.10's)

Can you post the outputs of 
```
apt-cache search libgtk1.2
```

---

### Post by Cory_Mittleider on 2014-05-04
I'm not sure.  Everywhere I've read indicates that 1.2 is long gone by 14.04.

Output
```
cory@cory-laptop:~$ apt-cache search libgtk1.2
libgtk1.2-common - Common files for the GTK+ library
```

---

### Post by monkeybrain20122 on 2014-05-04
> **Cory_Mittleider said:**
> I'm not sure.  Everywhere I've read indicates that 1.2 is long gone by 14.04.

Output
```
cory@cory-laptop:~$ apt-cache search libgtk1.2
libgtk1.2-common - Common files for the GTK+ library
```

Hmm.. I just ran the same command in my 14.04 and it turned up nothing (as I would expect)

Do you have synaptic? From synaptic you can check where the package comes from.

---

### Post by John_Gabo on 2014-06-06
I've downloaded this archive from the packages link said above: [https://launchpad.net/~mati75/+archive/lubuntu-testing/+files/gtk%2B1.2_1.2.10.orig.tar.gz](https://launchpad.net/~mati75/+archive/lubuntu-testing/+files/gtk%2B1.2_1.2.10.orig.tar.gz) Is there a way to install it?

---

