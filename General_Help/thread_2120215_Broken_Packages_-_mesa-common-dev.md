---
title: "Broken Packages - mesa-common-dev"
date: 2013-02-26
forum: General Help
---

### Post by ccdwiu on 2013-02-26
Hi, I'm trying to install the mesa-common-dev package. When I try to install, I get the following output:

```
chris@jarvis:~$ sudo apt-get install mesa-common-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  mesa-common-dev: Depends: libdrm-dev but it is not going to be installed
E: Broken packages

```

Trying to install libdrm-dev, I get this output:
```

chris@jarvis:~$ sudo apt-get install libdrm-dev 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libdrm-dev: Depends: libdrm2 (= 2.4.18-1ubuntu3) but 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~lucid is to be installed
              Depends: libdrm-intel1 (= 2.4.18-1ubuntu3) but 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~lucid is to be installed
              Depends: libdrm-radeon1 (= 2.4.18-1ubuntu3) but 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~lucid is to be installed
              Depends: libdrm-nouveau1 (= 2.4.18-1ubuntu3) but 2.4.23+git20110119.550fe2ca-0ubuntu0sarvatt~lucid is to be installed
E: Broken packages
```

Does anybody have any ideas? I am not sure why it is trying to install 2.4.23. It could be because this version is for Ubuntu 11.04. I actually downgraded from 11.04 to 10.04. Could this be the reason? Does anybody know how to fix this?

---

### Post by Bucky Ball on 2013-02-26
*Thread moved to **General Help**.*

***Reason: ***"Installation & Upgrades: For questions about upgrading and installation of your new Ubuntu OS."

11.04 has reached end of life and is no longer supported so wouldn't go there. 10.04 LTS is supported until April this year. Perhaps try 12.04 LTS. Trying to use the 11.04 software in 10.04 LTS would possibly be the cause of your issue.

BTW, when you said you 'downgraded' I'm presuming you did a fresh install of 10.04 LTS?

---

### Post by ccdwiu on 2013-02-26
> **Bucky Ball said:**
> *Thread moved to **General Help**.*

***Reason: ***"Installation & Upgrades: For questions about upgrading and installation of your new Ubuntu OS."

11.04 has reached end of life and is no longer supported so wouldn't go there. 10.04 LTS is supported until April this year. Perhaps try 12.04 LTS. Trying to use the 11.04 software in 10.04 LTS would possibly be the cause of your issue.

BTW, when you said you 'downgraded' I'm presuming you did a fresh install of 10.04 LTS?

Thanks.

I was running 10.04 and upgraded to 11.04 when it came out. I didn't like it and just installed 10.04 on top of 11.04. Probably not a good move.

---

### Post by Bucky Ball on 2013-02-26
Well, the fresh 10.04 LTS install should have killed everything in the 11.04 partition if it was installed to the same one that 11.04 lived on. 

You can do an upgrade from LTS to LTS without too much trouble through Update Manager. Thus, 10.04 to 12.04 LTS is easy. But, be aware, as you probably are, that 12.04 LTS uses Unity as the default desktop environment, not Gnome. I have heard of the automatic upgrade causing issues because of this (and other things). If you don't like or haven't tried Unity I suggest trying it from the LiveCD first. You can always install and immediately install another desktop environment if you don't like Unity. Many have simply swapped to Xubuntu as an alternative. 

I generally find the easiest, quickest and least problematic way is to do a fresh install.

---

### Post by ccdwiu on 2013-02-26
Thanks for the info. I agree and am going to do a fresh install.

Is there an easy way to save my home directory (I don't have an external hard drive, and unfortunately already have 4 primary partitions on my HDD) ?

---

### Post by Bucky Ball on 2013-02-26
There's easy ways to save it but where are you going to save it to?

---

### Post by cortman on 2013-02-26
And if Unity isn't your cup of tea, try [Xubuntu]("http://xubuntu.org/") when you reinstall.

---

### Post by ccdwiu on 2013-02-26
> **Bucky Ball said:**
> There's easy ways to save it but where are you going to save it to?

That is the problem! I think I'll just get rid of my Win7 partition as I don't use it anymore. I'd like a separate partition for my home directory so it is easier for me to change distros.

Also, I think I'm going to install either Cinnamon or Mate. Any other suggestions?

---

### Post by Bucky Ball on 2013-02-26
If you want to use a separate partition for /home you need to click 'Something Else' when you get to the partitioning section of the install and partition manually. If you delete the Windows partition before install then you will see the free space it left clearly and will be able to set that up while reinstalling over the current Ubuntu partition.

Xubuntu is my flavour but I suggest you install whatever you like, then try as many desktop environments as you like (Xubuntu uses xfce4) rather than installing any '*buntu-desktop' to try things.

Once you find what you like and what works best for you then perhaps reinstall the system exactly as you like it. (I think Linux Mint uses Cinammon as default but I could be wrong ... or is it Mate?). 

Good luck. ;)

PS: I'd stick with 12.04 LTS whichever flavour you choose.

---

