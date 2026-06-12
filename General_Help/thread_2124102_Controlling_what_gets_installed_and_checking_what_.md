---
title: "Controlling what gets installed and checking what is installed with apt-get"
date: 2013-03-09
forum: General Help
---

### Post by 7o7YlUcb on 2013-03-09
Is there a general way to tell if an installed app is 32-bit or 64-bit?

And if I'm on 64-bit ubuntu, do 64-bit versions of apps automatically get installed if there is one available (using the sudo apt-get install)? I.e. is apt-get intelligent enough to figure out that the 64-bit version is probably what I want, or do I need to set an extra flag or something to get the 64-bit version?

I recently installed imagemagic using the following command:
sudo apt-get -y install imagemagick

On the imagemagick website it offers different types (low memory version versus higher accuracy one) and you can download the appropriate .rpm. Presumably this choice is also available through apt-get. Is there a way to query what options for install there are available through apt-get? Or is it more usual that apt-get can only install one thing and you need another repository or something to access a different version of the app?

---

### Post by Paqman on 2013-03-09
> **RevRhubar said:**
> is apt-get intelligent enough to figure out that the 64-bit version is probably what I want

Every package in the repos is available in both 32-bit and 64-bit. The package manager will always install the right one for your system.

> 
Presumably this choice is also available through apt-get.

Not really. Generally only one version of each package gets built.

---

### Post by ibjsb4 on 2013-03-09
You may want to use one of the advance package managers.  I like Synaptic Package Manager.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=synaptic+package+manager&sa=Search&cof=FORID:9)

Ubuntu uses .deb packages although there are installers for .rpm, I do not recommend it or at best use it as a last resort.  You can either go to the maintainer's site or you can get updated packages not offered in the software center by using the Ubuntu PPA's.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+use+ppa&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=how+to+use+ppa&sa=Search&cof=FORID:9)

---

### Post by oldos2er on 2013-03-10
If you're running 64-bit and you want to install the 32-bit version of a program in the repositories, you'd run ```
sudo apt-get install imagemagick:i386
```  This assumes you have ia32-libs-multiarch already installed.

---

