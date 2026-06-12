---
title: "Can two versions of libpng coexist?"
date: 2019-05-26
forum: General Help
---

### Post by abdoo-892005 on 2019-05-26
Hi,

I am using Ubuntu 18.04 and I have libpng16 installed. However, one of the programs I would like to use needs libpng12 which doesn't exist anymore in the repositories.

I have found it as a deb package and, in a VM, tried installing it alongside libpng16 and everything seemed to be working really well, but I want to know if this could create any issues in the future before I deploy it on my actual machine.

Is it okay to have both versions installed, especially now that libpng12 is not officially supported in the newer versions of Ubuntu?

---

### Post by TheFu on 2019-05-26
This is a perfect reason to use a snap or flatpak for that tool you want.  Each program runs inside a self-contained "container" that keeps all the dependencies separate from other parts of the system.

In the olden-days, we'd install the non-standard libraries in a "lib/" directory next to the program "bin/" directory, and create a little script that modified the LD_LIBRARY_PATH with this new "lib/" first in the order. That way, when the program went to load the shared library, it would find the one it wanted first.  You can read up on LD_LIBRARY_PATH.  It is basically just like the PATH, just for shared libraries.

If the exact filename is libpng12.so, then there is little chance of unintended interactions between it and libpng16.so. Should be fine.

However, if the numbers have periods before them and symbolic links are made from libpng.12.so to libpng.so, then that will bring havoc to your system because it would replace the symlink from libpng.16.so.  I don't think this is how libpngXX works.  They know there needs to be multiple versions on systems for compatibility reasons.
I checked my system and found this:
```
/lib/x86_64-linux-gnu$ ll libpng*
lrwxrwxrwx 1 root root     18 Feb 28 15:03 libpng12.so.0 -> libpng12.so.0.54.0
-rw-r--r-- 1 root root 149904 Jul 10  2018 libpng12.so.0.54.0
```

So the libpng12.so interaction would be minimal. See the symlink?  

However, any the dependencies for that library could bring unintended interactions. I don't know if there are any dependencies.  Some libraries have lots of dependencies on other libraries and some strive to have ZERO dependencies.  /usr/share/doc/libpng12-0/README.Debian explains a little. I bet the v16 README explains some too, but don't have that on any of my systems.

---

### Post by abdoo-892005 on 2019-05-26
The problem is the tool I want to use doesn't have a snap or a flatpak version. It is a proprietary, portable (as in no installation required) 3D rendering engine. One option would be to build a flatpak for it myself, but I haven't done that before so I don't know how hard would that be.

I will probably have to look into it a bit more to see if installing libpng12 could create any issues, as I don't want to risk it.

---

### Post by TheFu on 2019-05-26
> 
If the exact filename is libpng12.so, then there is little chance of unintended interactions between it and libpng16.so. Should be fine.
as said above.  I wouldn't worry.

[https://tutorials.ubuntu.com/tutorial/create-your-first-snap](https://tutorials.ubuntu.com/tutorial/create-your-first-snap)

---

### Post by mc4man on 2019-05-26
> Can two versions of libpng coexist?
Yes, you can have two different libpng versions installed (the shared library, not the -dev). Any app that links to libpng16-16, (libpng16.so.0)  will not be affected by the presence of libpng12-0 (libpng12.so.0).
Whether an app that requires libpng12 can be installed is different story..

ex.
> sudo apt install '/home/doug/Downloads/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb'
.....
The following NEW packages will be installed:
  libpng12-0
0 upgraded, 1 newly installed, 0 to remove and 86 not upgraded.
Need to get 0 B/116 kB of archives.
After this operation, 285 kB of additional disk space will be used.
Get:1 /home/doug/Downloads/libpng12-0_1.2.54-1ubuntu1.1_amd64.deb libpng12-0 amd64 1.2.54-1ubuntu1.1 [116 kB]
Selecting previously unselected package libpng12-0:amd64.
(Reading database ... 335277 files and directories currently installed.)
Preparing to unpack .../libpng12-0_1.2.54-1ubuntu1.1_amd64.deb ...
Unpacking libpng12-0:amd64 (1.2.54-1ubuntu1.1) ...
Setting up libpng12-0:amd64 (1.2.54-1ubuntu1.1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...

---

### Post by abdoo-892005 on 2019-05-27
Thank you very much, guys. I will proceed with installing it.

---

