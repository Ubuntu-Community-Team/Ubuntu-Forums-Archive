---
title: "[SOLVED] root@Laptop:/media/sda2/Downloads/xwinwrap# uname -r
xlibc6-dev won't insta"
date: 2008-04-12
forum: General Help
---

### Post by Kissell on 2008-04-12
okay, i'm not entirely a newbie, i have worked in IT for over a decade, but I am fairly new to linux, and can't seem to get the xlibc6-dev to install, which I need for several apps I want to compile.

I'm running ubuntu 7.10 Gutsy Gibbon 64-bit server on a laptop, however, i have upgraded the kernel to hardy so that my built-in wireless card and sd card reader would work.  

When i try to install the libc6-dev package, it tells me it depends on a different version of libc6 (an older one) than what I have installed.  And anytime I try to install libc6 it tells me I already have the newest one...  :(

>   libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed

Anyone know how I get libc6-dev installed?  I've found a .deb package and tried to install it, but it told me that it wouldn't install because it was the i386 version.  :(

Here's the full command shell output:
> root@Laptop:/media/sda2/Downloads/xwinwrap# apt-get -f install libc6-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.6.1-1ubuntu10) but 2.7-10ubuntu3 is to be installed
E: Broken packages


---

### Post by jpkotta on 2008-04-12
Install the build-essential virtual package.  It depends on all of the packages you absolutely need for development, and apt will install all of the dependencies for you.

---

### Post by Kissell on 2008-04-12
Yeah, i've tried, that, and it's just part of the loop of errors...  build-essential requires libc6-dev as a dependency, so it won't install, and back to the original problem.  :(

> root@Laptop:/# sudo apt-get -f install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages


---

### Post by jpkotta on 2008-04-13
When you updated your kernel, did you also update your libc?  I'm pretty sure you can update the two independently, even though they are tightly coupled.  Post the results of ```
dpkg -l libc6*
```

---

### Post by Kissell on 2008-04-13
Unfortunately, I do not know, I blindly followed a python hardy.pl script I found in a forum to upgrade the kernel, and it did fix my wireless card and my SD card reader built into the laptop...  but I suspect it caused this problem.

> root@Laptop:/# dpkg -l libc6*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libc6          2.7-10ubuntu3  GNU C Library: Shared libraries
un  libc6-dev      <none>         (no description available)
un  libc6-dev-i386 <none>         (no description available)
ii  libc6-i386     2.7-10ubuntu3  GNU C Library: 32bit shared libraries for AM
un  libc6.1        <none>         (no description available)


> root@Laptop:/# uname -r
2.6.24-15-generic


---

### Post by jpkotta on 2008-04-13
Yeah, it updated libc6.  But you're still using Gutsy repos, so it can't find the libc6-dev that matches the one you have installed.  I'd say your best bet is to upgrade completely to Hardy.  It's close to release, so it shouldn't be too flaky.  

Instructions at [https://help.ubuntu.com/community/HardyUpgrades](https://help.ubuntu.com/community/HardyUpgrades).  Search the forums for known issues.  Personally, I prefer the CDROM method, with a loopback mount so I don't need to burn it.  I like that method because I can use Bit Torrent and lighten the load on the Ubuntu servers, which get really slow around release time, and  I have a CD image if I do decide to burn it.

The alternative is to manually install all the packages you need.  You can find them at [http://packages.ubuntu.com/](http://packages.ubuntu.com/).

---

### Post by Kissell on 2008-04-15
thanks!

Technically that fixed my problem...  However, it broke my nvidia video setup, and i'm definately a novice when it comes to that stuff...  i got the video working again, but haven't been able to get compiz to give me the cube rotate that i loved...  :(

Liinux reminds me of that quote from judge dread...  "It's yours, when you can get it to work!"  So far I'm loving Ubuntu and it's now the only OS I run on any of my systems from server to laptop.  I know when it's working it is the best thing out there right now...  but i'm still not an expert at fixing it when it's broken...  

:guitar:

---

### Post by Kissell on 2008-04-16
new updates to the development version of hardy evidentally fixed my video driver and compiz cube rotate problem...  so everything's now working regarding this thread.

---

### Post by MaindotC on 2008-05-10
I'd like to reopen this thread.  I'm trying to follow [these directions]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide#Method_2:_Manual_Method") to install the latest ATI driver so hopefully my xorg.conf will be properly configured and my suspend feature will work.  I'm running into the same issue Kissell initially stated.

I did have the hardy repositories listed in sources.list file once because I was installing the latest kernel (I was using Hardy and the suspend feature worked but there are some bugs so I did a fresh, clean install of Gutsy till certain bugs are worked out).  I did the reverse of the directions given to me on [this post]("http://www.justubuntu.com/install_2_6_22-10_ubuntu") and things seem to be back to normal (new kernel gave me some problems) but I still see it in /lib/modules.

I tried installing the deb from the packages link, but in order to do that I would have to uninstall libc6 which gives nice little messages when you try and do that.  Can you help me get this done without a re-install?  Thanks!

---

