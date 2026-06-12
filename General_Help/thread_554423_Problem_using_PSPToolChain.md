---
title: "Problem using PSPToolChain"
date: 2007-09-19
forum: General Help
---

### Post by Newuser1111 on 2007-09-19
When I try to run it this error happens:

ERROR: Add /usr/local/pspdev/bin to your path before continuing.
../depends/check-pspdev.sh: Failed.

Does anyone know what's wrong?

---

### Post by apetresc on 2007-09-19
> **Newuser1111 said:**
> When I try to run it this error happens:

ERROR: Add /usr/local/pspdev/bin to your path before continuing.
../depends/check-pspdev.sh: Failed.

Does anyone know what's wrong?

Quite simply, you need to add /usr/local/pspdev/bin to your path before continuing, just like it says. You can do this with:```
export PATH=$PATH:/usr/local/pspdev/bin
``` (If you want this change to be persistent, add this to your .bash_profile file)

---

### Post by Newuser1111 on 2007-09-19
New error:
ERROR: Set $PSPDEV before continuing.

---

### Post by Newuser1111 on 2007-09-19
Did some stuff and now New error:

/home/name/Desktop/psptoolchain/toolchain.sh: line 5: dirname: command not found
/home/name/Desktop/psptoolchain/toolchain.sh: line 8: mkdir: command not found
ERROR: Could not create the build directory.

---

### Post by Newuser1111 on 2007-09-19
Please help me!

---

### Post by apetresc on 2007-09-19
> **Newuser1111 said:**
> Did some stuff and now New error:

/home/name/Desktop/psptoolchain/toolchain.sh: line 5: dirname: command not found
/home/name/Desktop/psptoolchain/toolchain.sh: line 8: mkdir: command not found
ERROR: Could not create the build directory.
You probably messed up your path when you added the pspdev folder to it, since dirname and mkdir are core Unix utilities that Ubuntu would not run without.

What is the output of ```
echo $PATH
``` right before you run that command?

---

### Post by Newuser1111 on 2007-09-19
echo $PATH gives:
/usr/local/pspdev/bin

---

### Post by Newuser1111 on 2007-09-19
Is that what I should be getting?

---

### Post by apetresc on 2007-09-19
> **Newuser1111 said:**
> echo $PATH gives:
/usr/local/pspdev/bin
Yeah, there's your problem. Are you sure you typed```
export PATH=$PATH:/usr/local/pspdev/bin
``` and not ```
export PATH=/usr/local/pspdev/bin
```?

EDIT:> Is that what I should be getting? No, it's not, which is why I suspect you typed my earlier path command wrong.

---

### Post by Newuser1111 on 2007-09-19
now echo $PATH is giving:
/usr/local/pspdev/bin:/usr/local/pspdev/bin

---

### Post by apetresc on 2007-09-19
> **Newuser1111 said:**
> now echo $PATH is giving:
/usr/local/pspdev/bin:/usr/local/pspdev/bin

Right, because your path is gone. Close whichever terminal you had this running in, and go through the whole process again. When it gets to the PATH=$PATH:/usr/local/pspdev/bin part, make sure you type the right thing in. When you type "echo $PATH", you should get a fairly long list of folders, at the end of which should be /usr/local/pspdev/bin.

---

### Post by Newuser1111 on 2007-09-19
Now this error:
ERROR: Add /usr/local/pspdev/bin to your path before continuing.
../depends/check-pspdev.sh: Failed.

And this:
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/pspdev/bin:/usr/local/pspdev/bin:/usr/local/pspdev/bin:/usr/local/pspdev/bin:/bin


I closed the terminal, I'm using the one I found in Accessories.

---

### Post by Newuser1111 on 2007-09-19
Do I have to double post to get an answer?

I'm trying to get this working as soon as possible.

---

### Post by apetresc on 2007-09-19
> **Newuser1111 said:**
> Do I have to double post to get an answer?
No, but patience would be good. I have four major assignments due Friday so I can't dedicate *all* my time to debugging strangers' problems on the internet :)

It seems that the entry is in your path now, as it should be. If it's still telling you it's not, then probably you are missing the proper utilities.

What is the output of ```
ls -al /usr/local/pspdev/bin
```?

---

### Post by Newuser1111 on 2007-09-19
ls -al /usr/local/pspdev/bin:

total 8
drwxr-xr-x 2 root root 4096 2007-09-18 21:29 .
drwxr-xr-x 3 root root 4096 2007-09-18 21:29 ..

---

### Post by apetresc on 2007-09-19
Aha, that's a problem. You haven't actually installed the pspSDK to /usr/local/pspdev/bin. You need it, and once it's built that folder will contain psp-gcc, psp-ld, psp-g++, etc.

If you have already built them somewhere else, it should just require a "sudo make install" in the build directory.

---

### Post by Newuser1111 on 2007-09-19
I don't think they are built,
Here's the place I got it:
[http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2]("http://ps2dev.org/psp/Tools/Toolchain/psptoolchain-20070626.tar.bz2")

So what do I do?

---

### Post by Newuser1111 on 2007-09-19
Now I ran a diffrent file:
 sudo /home/name/Desktop/psptoolchain/toolchain-sudo.sh

Now when I do:
 ls -al /usr/local/pspdev/bin

The results are:
total 61272
drwxr-xr-x  2 root root     4096 2007-09-19 22:02 .
drwxr-xr-x 11 root root     4096 2007-09-19 21:24 ..
-rwxr-xr-x  1 root root    10911 2007-09-19 21:51 bin2c
-rwxr-xr-x  1 root root    17743 2007-09-19 21:51 bin2o
-rwxr-xr-x  1 root root    10952 2007-09-19 21:51 bin2s
-rwxr-xr-x  1 root root    10309 2007-09-19 21:51 mksfo
-rwxr-xr-x  1 root root    12105 2007-09-19 21:51 pack-pbp
-rwxr-xr-x  1 root root  2292635 2007-09-19 21:12 psp-addr2line
-rwxr-xr-x  2 root root  2270277 2007-09-19 21:12 psp-ar
-rwxr-xr-x  2 root root  3471744 2007-09-19 21:12 psp-as
-rwxr-xr-x  1 root root    59271 2007-09-19 21:51 psp-build-exports
-rwxr-xr-x  2 root root   299637 2007-09-19 21:47 psp-c++
-rwxr-xr-x  1 root root  2255044 2007-09-19 21:12 psp-c++filt
-rwxr-xr-x  1 root root    24077 2007-09-19 21:51 psp-config
-rwxr-xr-x  1 root root   299370 2007-09-19 21:47 psp-cpp
-rwxr-xr-x  1 root root    32209 2007-09-19 21:51 psp-fixup-imports
-rwxr-xr-x  2 root root   299637 2007-09-19 21:47 psp-g++
-rwxr-xr-x  2 root root   298195 2007-09-19 21:47 psp-gcc
-rwxr-xr-x  2 root root   298195 2007-09-19 21:47 psp-gcc-4.1.0
-rwxr-xr-x  1 root root    15930 2007-09-19 21:47 psp-gccbug
-rwxr-xr-x  1 root root    74531 2007-09-19 21:47 psp-gcov
-rwxr-xr-x  1 root root 11588256 2007-09-19 22:02 psp-gdb
-rwxr-xr-x  1 root root 11588293 2007-09-19 22:02 psp-gdbtui
-rwxr-xr-x  1 root root  2595591 2007-09-19 21:12 psp-gprof
-rwxr-xr-x  2 root root  3035364 2007-09-19 21:12 psp-ld
-rwxr-xr-x  2 root root  2326627 2007-09-19 21:12 psp-nm
-rwxr-xr-x  1 root root  2804518 2007-09-19 21:12 psp-objcopy
-rwxr-xr-x  2 root root  2997124 2007-09-19 21:12 psp-objdump
-rwxr-xr-x  1 root root    39040 2007-09-19 21:51 psp-prxgen
-rwxr-xr-x  2 root root  2270268 2007-09-19 21:12 psp-ranlib
-rwxr-xr-x  1 root root   437265 2007-09-19 21:12 psp-readelf
-rwxr-xr-x  1 root root  3655281 2007-09-19 22:02 psp-run
-rwxr-xr-x  1 root root  2177190 2007-09-19 21:12 psp-size
-rwxr-xr-x  1 root root  2159301 2007-09-19 21:12 psp-strings
-rwxr-xr-x  2 root root  2804541 2007-09-19 21:12 psp-strip
-rwxr-xr-x  1 root root    12065 2007-09-19 21:51 unpack-pbp


Now is it installed?

---

### Post by Newuser1111 on 2007-09-19
So, how do I use it?

---

### Post by Maestro23 on 2007-09-19
> **Newuser1111 said:**
> So, how do I use it?

Do you have all the required software packages installed like it said in the Documentation?  Didn't you make one post concerning this already?

---

### Post by Newuser1111 on 2007-09-19
If there's another like this one then don't mind it.

I think it installed everything it needed to.

---

### Post by Jet8225 on 2007-12-14
Mine's giving that same thing three times

---

