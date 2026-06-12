---
title: "Installing SEP 12.1.5 Ubuntu 14.10 x64"
date: 2014-10-29
forum: General Help
---

### Post by minhgi on 2014-10-29
I having trouble installing Symantec Endpint Protection 12.1.5 for Ubuntu 14.10.  I am getting a x11 library missing.   Even thought, I have installed libx11-dev.  These are the error message after executing the install.sh.  Thanks in advance.

 root@ubuntu:/home/minhgi/Downloads/test# ./install.sh -i
Starting to install Symantec Endpoint Protection for Linux
Performing pre-check...
Warning:    X11 libraries are missing, GUI component will not be installed!
Pre-check succeeded
Begin installing virus protection component
(Reading database ... 323838 files and directories currently installed.)
Preparing to unpack .../test/./Repository/sep.deb ...
Missing package files: //../install.sh, please check the package and use a valid one.
Virus protection component failed to install, with error:  /home/minhgi/Downloads/test/./Repository/sep.deb
root@ubuntu:/home/minhgi/Downloads/test# ./install.sh -i
Starting to install Symantec Endpoint Protection for Linux
Performing pre-check...
Warning:    X11 libraries are missing, GUI component will not be installed!
Pre-check succeeded
Begin installing virus protection component
(Reading database ... 323838 files and directories currently installed.)
Preparing to unpack .../test/./Repository/sep.deb ...
Missing package files: //../install.sh, please check the package and use a valid one.
Virus protection component failed to install, with error:  /home/minhgi/Downloads/test/./Repository/sep.deb
root@ubuntu:/home/minhgi/Downloads/test#

---

### Post by leonid-shumakov on 2014-11-05
Check logs:

cat ~/sep-install.log
cat ~/sepf-install.log

Seems sep.deb(preinst script) uses empty $PWD

Fastest way - copy endpoint files to root directory(/, not /root) and execute install.sh from there.

---

