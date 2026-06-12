---
title: "ATI driver install problems + tri-screen"
date: 2007-10-05
forum: General Help
---

### Post by Elusid on 2007-10-05
Alright  so here is my problem. I have 2 2900XT GDDR4 1GB installed in my computer and I'm trying to install the ATI drivers that just came out using this guide

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually)

and it all works up till this point
> 
Install .deb packages:
```

sudo dpkg -i xorg-driver-fglrx_8.41.7-1*.deb \
fglrx-kernel-source_8.41.7-1*.deb \
fglrx-amdcccle_8.41.7-1*.deb
```

    * Note: If you have a 64 bit install, the above dpkg command will likely complain that "Errors were encountered while processing: fglrx-amdcccle". This is because of a dependency of the amdccle package on 32 bit libraries. If you recieve this error, issue the following command after the above dpkg command, which will force the installation of all of the 32 bit dependencies, and then the amdccle pacakge: 

and when I put that into the console I get this message

> 
dpkg: error processing xorg-driver-fglrx_8.41.7-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.41.7-1*.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.41.7-1*.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 xorg-driver-fglrx_8.41.7-1*.deb
 fglrx-kernel-source_8.41.7-1*.deb
 fglrx-amdcccle_8.41.7-1*.deb


any ideas what's going on here? Is there any more information that I need to give you guys to help me? Also I'm running 3 screens here and I was just wondering how I would get all 3 of them working once I get the drivers up and running. Thanks for the help.

---

### Post by Ub1476 on 2007-10-05
If you are running a 65-bit OS (AMD64) did you use the the following command?

```
sudo apt-get install -f
``` 

If you are using Ubuntu, you can install the drivers by going to System>Administration>Restricted Driver Manager.

---

### Post by Elusid on 2007-10-05
> **Ub1476 said:**
> If you are running a 65-bit OS (AMD64) did you use the the following command?

```
sudo apt-get install -f
``` 

If you are using Ubuntu, you can install the drivers by going to System>Administration>Restricted Driver Manager.

I'm running the 32 bit version of Ubuntu and I first did the restricted drivers but it made my whole screen artifact. I would drag something across the screen and it would streak and stuff would be there but not be visible etc etc.

---

### Post by strabes on 2007-10-05
Is there a specific reason you're using this difficult method to install the drivers? There are much easier ways of doing it, one of which is linked to in my signature.

---

