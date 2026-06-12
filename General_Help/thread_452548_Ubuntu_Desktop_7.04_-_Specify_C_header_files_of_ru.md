---
title: "Ubuntu Desktop 7.04 - Specify C header files of running kernel for VMWare Sever"
date: 2007-05-23
forum: General Help
---

### Post by milu04 on 2007-05-23
Hi all,

I am trying to install VMWare server on my new Ubuntu Desktop 7.04 with root access. When I run "perl vmware-install.pl" and have a question from installation process:
"What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]". 

I have checked my directory tree and I find out that I have "/usr/src/linux-headers-2.6.20-15/include/", then I specify this to answer above question. 

The installation process outputs: "The directory of kernel headers (version 2.6.20-15) does not match your running kernel (version 2.6.20-15-server)"

Could you please tell me how to fix this? How to get header files for version 2.6.20-15-server? 

I am a newbie. Thank you very much for your help.

---

### Post by wordsmithereens on 2007-05-23
I've used this reference to successfully install VMWare Server on 2 different machines...

[http://ubuntuforums.org/showpost.php?p=2384779&postcount=52](http://ubuntuforums.org/showpost.php?p=2384779&postcount=52)


> **milu04 said:**
> Hi all,

I am trying to install VMWare server on my new Ubuntu Desktop 7.04 with root access. When I run "perl vmware-install.pl" and have a question from installation process:
"What is the location of the directory of C header files that match your running kernel? [/usr/src/linux/include]". 

I have checked my directory tree and I find out that I have "/usr/src/linux-headers-2.6.20-15/include/", then I specify this to answer above question. 

The installation process outputs: "The directory of kernel headers (version 2.6.20-15) does not match your running kernel (version 2.6.20-15-server)"

Could you please tell me how to fix this? How to get header files for version 2.6.20-15-server? 

I am a newbie. Thank you very much for your help.

---

