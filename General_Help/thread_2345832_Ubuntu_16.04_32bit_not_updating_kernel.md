---
title: "Ubuntu 16.04 32bit not updating kernel"
date: 2016-12-08
forum: General Help
---

### Post by John_Carver on 2016-12-08
The current kernel version is 3.13.0-93 in my 32 bit installation
Appears the version should be in the 4.4 range.

My 64 bit version currently has a kernel of 4.4.0-53-generic

How do I update the 32bit version to the current kernel?

thanks

---

### Post by oldfred on 2016-12-08
Your 3.13 is 14.04, not 16.04.

Post these:
 #Current kernel:
uname -a
# kernels, shows older also?
dpkg --list | grep linux-image 

Do you get errors?
sudo apt-get update
sudo apt-get upgrade

---

### Post by John_Carver on 2016-12-08
I realize this is the wrong kernel and need 14.04 version
$ dpkg --list | grep linux-image 
ii  linux-image-3.13.0-93-generic                3.13.0-93.140                                 i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic          3.13.0-93.140                                 i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
john@john-desktop:~$ 

$ uname -a
Linux john-desktop 3.13.0-93-generic #140-Ubuntu SMP Mon Jul 18 21:20:08 UTC 2016 i686 athlon i686 GNU/Linux
john@john-desktop:~$ 

No errors on update or upgrade

---

### Post by John_Carver on 2016-12-08
Correction
This message appears at the end of the update
[http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease:](http://security.ubuntu.com/ubuntu/dists/precise-security/InRelease:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)
W: [http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:](http://archive.canonical.com/ubuntu/dists/precise/Release.gpg:) Signature by key 630239CC130E1A7FD81A27B140976EAF437D05B5 uses weak digest algorithm (SHA1)

---

### Post by oldfred on 2016-12-08
I have never installed a newer kernel into a distribution than what the default is.

Your 3.13 is correct for 14.04 or 14.04.1. 

They do have the HWE - Hardware Enablement Stacks which are to allow the LTS versions to use a newer kernel so newer hardware is supported. But if you have full hardware support with your version, you should not need the Enablement Stack.

[https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_14.04_LTS_-_Trusty_Tahr)

If you really want newer kernel, probably easier to just upgrade to newer version of Ubuntu.
And if system is less than about 10 years old and has about 2GB or more of RAM,  you may want the 64 bit verison.

---

### Post by John_Carver on 2016-12-08
Thanks for the assistance
Guess this is a freak instance 
Appears I will upgrade to 16.10 for a fix and leave LTS

---

### Post by John_Carver on 2016-12-08
Solved but don't have the trick to indicate it

---

### Post by mörgæs on 2016-12-09
Did you read Oldfred's signature?

---

