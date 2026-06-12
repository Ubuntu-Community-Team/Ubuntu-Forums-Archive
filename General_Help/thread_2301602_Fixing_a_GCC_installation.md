---
title: "Fixing a GCC installation"
date: 2015-11-03
forum: General Help
---

### Post by stan22 on 2015-11-03
Hi folks,

I on Ubuntu 14.10 on a virtual machine and I am trying to get GCC (4.9 or, if possible 5.2) to run (a .sh file does some automated installation for me, and at some point it terminates due to an error regarding GCC: "c compiler cannot create executables"). I simply want to compile a helloworld.cpp file to see where there might be a problem, but I can't get GCC to work. 
 
It says "The program 'gcc' is currently not installed. You can install it by typing: sudo apt-get install gcc". Doing this, I get the response "E: Package 'gcc' has no installation candidate." 
When I try "sudo apt-get install gcc-4.9" I get "0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded". Trying to install g++ returns "E: Unable to correct problems, you have held broken packages".
Neither has is the Ubuntu Software Center been of any use. In addition I tried to install GCC 5.2 manually, but this requires me to use "subversion" which I cannot install either (".. no installation candidate.").

Any help is appreciated. Thanks a lot!

btw., what is that fuzz with the versions all about? What's the difference between gcc and gcc-4.9 with respect to the software installed on my computer?

---

### Post by deadflowr on 2015-11-03
Upgrade your Ubuntu version from 14.10 to something newer.
Either 15.04, 15.10.

14.10 is no longer supported so the package archives have been moved.
Which is why you are getting no installation candidate.

Alternatively, you can install 14.04, which has long-term-support.

Best option is to simply download a currently supported version and re-install.

---

