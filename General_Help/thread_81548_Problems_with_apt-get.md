---
title: "Problems with apt-get"
date: 2005-10-24
forum: General Help
---

### Post by Kimppa on 2005-10-24
Hello

I'm having huge problems with apt-get, which hinders me from even updating my system.
I run "apt-get update" normally, no problem, but when I run upgrade, I get this

> 
root@kleppane:/home/kimppa # apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  xlibmesa-gl-dev: Depends: xlibmesa-gl (= 6.8.2-10.1) but 6.8.2-10 is installed
E: Unmet dependencies. Try using -f.
root@kleppane:/home/kimppa #


Right, so now I try to run -f install

> 
root@kleppane:/home/kimppa # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  xlibmesa-gl
The following packages will be upgraded:
  xlibmesa-gl
1 upgraded, 0 newly installed, 0 to remove and 44 not upgraded.
116 not fully installed or removed.
Need to get 0B/308kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]?

Preconfiguring packages ...
(Reading database ... 135255 files and directories currently installed.)
Preparing to replace xlibmesa-gl 6.8.2-10 (using .../xlibmesa-gl_6.8.2-10.1_i386.deb) ...
Unpacking replacement xlibmesa-gl ...
dpkg: error processing /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb (--unpack):
 trying to overwrite `/usr/X11R6/lib/libGL.so.1.2', which is also in package fglrx-6-8-0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/xlibmesa-gl_6.8.2-10.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kleppane:/home/kimppa #


Any idea how to fix this problem?

Thank you in advance,

Kimppa

---

### Post by Xian on 2005-10-25
You need to first remove the fglrx package & then install xlibmesa-gl.
Next you can reinstall fglrx.

---

### Post by Kimppa on 2005-10-25
> 
root@kleppane:/home/kimppa # apt-get remove fglrx-6-8-0
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  xlibmesa-gl-dev: Depends: xlibmesa-gl (= 6.8.2-10.1) but 6.8.2-10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@kleppane:/home/kimppa #


Hmmm... weird, won't remove it

---

### Post by Xian on 2005-10-26
Apt generally won't add or remove pkgs when you have unmet dependencies on your system. You need to first resolve those, and the place to start is by issuing the command it suggested to you and then trying to determine what needs to be done.

$ sudo apt-get -f install

---

