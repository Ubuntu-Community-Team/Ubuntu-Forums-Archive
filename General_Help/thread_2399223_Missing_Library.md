---
title: "Missing Library"
date: 2018-08-23
forum: General Help
---

### Post by orhan.1692 on 2018-08-23
Hello Everyone,
I installed a software on my XUBUNTU. When I tried to execute the bin file, there were some missing libraries and I found most of those on the internet, however there is still one which is "libSculptorInterface.so.1". The problem is that I could not achieve to find it and now I cannot run the program. 
I tried to install it with "sudo apt-get install <missinglibraryname>", but it did not work either. 
I hope that someone can help me to figure out this problem. 
Thanks in advance...
Orhan

---

### Post by again? on 2018-08-23
What program, where did you get it and how are you installing it?

---

### Post by orhan.1692 on 2018-08-23
Hey guber2,
It is a CFD program called as CONVERGE-CFD. Actually I installed Converge-Studio for pre and post-processing. There was an archive file. I extracted the files in it and install the sofware by using ./INSTALL command, as there was an install file. The problem occurred later, when I tried to execute the bin file in the installation directory. It gave me a warning related to the missing libraries. I installed most of those libraries, yet there is still one more. 
I tried to install the library by writing sudo apt-get install <library's name>, however it didn't work.

---

### Post by steeldriver on 2018-08-23
Are you sure you are meant to execute the bin file directly? My guess is that libSculptorInterface.so.1 is a vendor supplied library, and there is a "wrapper script" that sets an appropriate library path so that the linker can find it, then runs the binary

At least, that's a fairly common way to distribute 3rd party software of this sort

---

### Post by orhan.1692 on 2018-08-24
Hey steeldriver,

I dunno that I used the right word in my explanation. What I did was to try running the bin file by writing ./file name_bin in Terminal. Thereafter it gave me the error below;

error while loading shared libraries: libSculptorInterface.so.1: cannot open shared object file: No such file or directory

I used ldd path/to/filename/filename_bin to see which libraries are missing and only that library was not found.

libSculptorInterface.so.1 => not found

What I can do for solving this problem. I cannot run the software due to this missing library. 

Best Regards...

Orhan

---

