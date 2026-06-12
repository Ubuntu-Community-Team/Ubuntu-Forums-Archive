---
title: "Install NI labview environment for GPIB-USB-HS"
date: 2008-05-23
forum: General Help
---

### Post by vishnumrao on 2008-05-23
I am trying to installl the Labview environment for a GPIB. Model: GPIB-USB-HS

But the NI software supports only rpm based distros. 

```

adm@adm-desktop:~/gpib$ sudo ./INSTALL --nodeps

*****************************************************************************
  NI-488.2 Distribution
     version 2.5.1f0 for Linux/x86 32-bit
*****************************************************************************

*****************************************************************************
   Warning: --nodeps is an unsupported option.
            Installing without dependency checking is dangerous.
            Only use this option if you know what you are doing.
*****************************************************************************
National Instruments products support the following Linux distributions:
   Mandriva Linux Official
   SUSE Linux
   Red Hat Enterprise Linux WS
Refer to README.txt for the latest information at the time of release.
Refer to www.ni.com/linux for the most recent information about Linux
support at National Instruments.

Continue? [Yn] y

Checking required install tools...
Checking installer tool versions...
rpm        4.4.1 can be used with a default installation path
tar        1.16
Checking dependencies...
glibc      2.5 
Unpacking install files to /tmp/NI4882-2.5.1f0.install...

******************************** ERROR ****************************************
* Kernel source in /lib/modules/2.6.20-16-generic/build does not appear to be
* for the 2.6.20-16-generic kernel.
* Ensure that kernel source for the 2.6.20-16-generic kernel is installed
* and configured.  Refer to the README file for the product you are           *
* installing for information about configuring your kernel source.            *
******************************** ERROR ****************************************

Installer is aborted.

```

I tried installing using a --nodeps optons. But no luck. It says kernel-source is not installed. 

I tried installing all kernel-source packages using apt-get. But no luck till now. 

How can I install the required kernel sources and proceed?

---

### Post by bwhite82 on 2008-05-23
Make sure the following packages are installed:

build-essential and linux-headers-*

* The end of the package name depends on which kernel you have installed, you can check by issuing the command: uname -r

---

### Post by vishnumrao on 2008-05-23
Thanks for your reply. The kernel I am running is: 2.6.20-16-generic

```


adm@adm-desktop:~/gpib$ sudo aptitude search linux-headers-2.6.20-16-generic
i   linux-headers-2.6.20-16-generic                                        - Linux kernel headers for version 2.6.20 on x86/x86_64                           
adm@adm-desktop:~/gpib$ sudo aptitude search build-essential
i   build-essential                                                        - informational list of build-essential packages                              


```

Yes, both packages you mentioned had already been installed.

---

### Post by bwhite82 on 2008-05-23
"aptitude search" shows any packages available, not just those installed. Please forgive, I must ask again, are you sure that they are installed?

Edit: Another question I have. Do you have a .rpm file to install this instead of the shell script? If so, you can use the program "alien" (available in the repos) to convert it to a .deb package and install it that way.

---

### Post by vishnumrao on 2008-05-23
The "i" that shows up when you do a aptitude search means its installed (I believe its true, I have noticed it when I do a "aptitude search", immediately after I had installed them).

Just to check, I tried to install them again

```

adm@adm-desktop:~/gpib$ sudo apt-get install linux-headers-2.6.20-16-generic build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.20-16-generic is already the newest version.
build-essential is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by bwhite82 on 2008-05-23
If you can't find an rpm package to install, try looking at this post I found: [http://forums.ni.com/ni/board/message?board.id=170&message.id=200997](http://forums.ni.com/ni/board/message?board.id=170&message.id=200997)

Edit: Also found this: [http://ubuntuforums.org/archive/index.php/t-726092.html](http://ubuntuforums.org/archive/index.php/t-726092.html)

---

