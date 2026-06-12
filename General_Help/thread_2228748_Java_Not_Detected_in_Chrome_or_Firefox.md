---
title: "Java Not Detected in Chrome or Firefox"
date: 2014-06-09
forum: General Help
---

### Post by ph3d on 2014-06-09
Hi Guys, 

I am running: 

```
eddie@evolution:~$ cat /etc/issue
Ubuntu 14.04 LTS \n \l
```

with the following version of Java installed: 


```
eddie@evolution:~$ java -version
java version "1.7.0_55"
OpenJDK Runtime Environment (IcedTea 2.4.7) (7u55-2.4.7-1ubuntu1)
OpenJDK 64-Bit Server VM (build 24.51-b03, mixed mode)
eddie@evolution:~$ 

```
I also have installed the icedtea plugin: 

Anything I need to do to re-enable Java support I have no support in either firefox from the day I installed 14.04 and it was working in chrome but now it is is not working in either.

Cheers!

---

### Post by slickymaster on 2014-06-11
NPAPI (Netscape Plugin Application Programming Interface) was dropped for Linux in Chrome 35 because of Aura. IcedTea and Oracle both use NPAPI, so it won't work until they are upgraded to the new system (don't expect that any time soon)

---

### Post by ph3d on 2014-06-11
Yeah - I have actually just found a read an article regarding this... Any idea about firefox? 

To downgrade chrome to 34 run the following commands in terminal: 

wget [http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_34.0.1847.137-1_amd64.deb](http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_34.0.1847.137-1_amd64.deb) (64bit)
or
wget [http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_34.0.1847.137-1_i386.deb](http://mirror.pcbeta.com/google/chrome/deb/pool/main/g/google-chrome-stable/google-chrome-stable_34.0.1847.137-1_i386.deb) (32bit)

sudo apt-get remove google-chrome-stable
mv ~/.config/chromium ~/.config/chromium-35-broken-java profile

sudo reboot - just to be sure - I had profile errors that where resolved on reboot

Launch another terminal after reboot and issue

sudo dpkg -i google-chrome-stable_34.0.1847.137-1_amd64.deb (64 bit version) 
or
sudo dpkg -i google-chrome-stable_34.0.1847.137-1_i386.deb

Enjoy having some Java again

---

### Post by ph3d on 2014-06-11
Preparing to unpack .../firefox_30.0+build1-0ubuntu0.14.04.3_amd64.de

Fixed Firefox for myself.. Not sure if it was yourself pushing something up the chain but thanks anyway..

---

