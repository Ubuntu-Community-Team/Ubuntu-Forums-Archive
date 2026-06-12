---
title: "Help Intel/ATI HD 5000 M Series Graphics"
date: 2013-01-02
forum: General Help
---

### Post by TheJeanValjean on 2013-01-02
Hi, I recently changed from using Windows 7 to using Ubuntu 12.10 32-bit and I was wondering if someone could explain to me what I am doing wrong. I am new to Ubuntu and Linux in general but I have been figuring my way around it pretty well up until now. 

So far I have installed proprietary drivers for my card multiple times and each time have successfully either gotten rid of unity or messed it up so bad that it couldn't even get me to the login screen. 

The computer I am using is an HP ENVY 14 from 2010 with Intel Integrated graphics and an ATI HD 5000 M series card (Madison) which doesn't appear to work with any of the many tutorials I have found online, the graphics driver that Ubuntu says I have is "Intel® Ironlake Mobile x86/MMX/SSE2". 

Right now I have a fresh install of Ubuntu 12.10 and have installed all updates and have the X.Org drivers installed for my card, and I get the system error message a few times after I log in stating that there are errors with the xorg drivers. Additionally I have tried the method laid out in [this]("http://asusm51ta-with-linux.blogspot.com/") link and got a GUI up and running that appeared to switch my cards but the driver that Ubuntu said I was running remained as the "Intel Ironlake Mobile" one whether I had "switched" to the discreet one of not. Furthermore I tried using vgaswitcheroo directly from the terminal and nothing was successful.  

At this point I just want to get my discreet card up and running, even if that means that I won't be able to use the integrated graphics as I don't particularly care if I have the "switchable" feature. Any information on this issue would be very helpful, I don't want to lose any more sleep over this. Thanks!

---

### Post by LinuxDomi on 2013-01-02
> **TheJeanValjean said:**
> Hi, I recently changed from using Windows 7 to using Ubuntu 12.10 32-bit and I was wondering if someone could explain to me what I am doing wrong. I am new to Ubuntu and Linux in general but I have been figuring my way around it pretty well up until now. 

So far I have installed proprietary drivers for my card multiple times and each time have successfully either gotten rid of unity or messed it up so bad that it couldn't even get me to the login screen. 

The computer I am using is an HP ENVY 14 from 2010 with Intel Integrated graphics and an ATI HD 5000 M series card (Madison) which doesn't appear to work with any of the many tutorials I have found online, the graphics driver that Ubuntu says I have is "Intel® Ironlake Mobile x86/MMX/SSE2". 

Right now I have a fresh install of Ubuntu 12.10 and have installed all updates and have the X.Org drivers installed for my card, and I get the system error message a few times after I log in stating that there are errors with the xorg drivers. Additionally I have tried the method laid out in [this]("http://asusm51ta-with-linux.blogspot.com/") link and got a GUI up and running that appeared to switch my cards but the driver that Ubuntu said I was running remained as the "Intel Ironlake Mobile" one whether I had "switched" to the discreet one of not. Furthermore I tried using vgaswitcheroo directly from the terminal and nothing was successful.  

At this point I just want to get my discreet card up and running, even if that means that I won't be able to use the integrated graphics as I don't particularly care if I have the "switchable" feature. Any information on this issue would be very helpful, I don't want to lose any more sleep over this. Thanks!

Now, this tutorial demonstrates the installation of AMD 12.11 beta drivers which work well with ubuntu 12.10 and they support the latest Xserver 1.13. 

If you have alredy installed the stable AMD drivers that don't work erase them:
On the desktop type ctrl+alt+t and type in
 ```
sudo apt-get autoremove --purge fglrx*
```
 for restart
  ```
sudo init 6
```
After that the computer uses the avaliable drivers. 

Now, again ctrl+alt+t and type
```
sudo apt-get install linux-headers-generic
```
restart

Log in, type

```
sudo add-apt-repository ppa:andrikos
sudo apt-get update
sudo apt-get install fglrx xserver-xorg-video-intel
sudo aticonfig --initial --force
```

restart (in my case it wouldn't boot on hte first restart but on the second it worked)

Because they are BETA, a sign in the bottom right corner will appear - to remove it folow the instructions on this link:

[http://www.ubunturoot.com/2012/07/remove-amdati-drivers-testing-only.html](http://www.ubunturoot.com/2012/07/remove-amdati-drivers-testing-only.html)

If that doesn't work here's a couple of handy links:

[http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10](http://askubuntu.com/questions/202857/cant-install-ati-proprietary-drivers-in-12-10)
[http://askubuntu.com/questions/204410/how-do-i-install-the-latest-ati-catalyst-video-drivers-in-ubuntu-12-10-quantal](http://askubuntu.com/questions/204410/how-do-i-install-the-latest-ati-catalyst-video-drivers-in-ubuntu-12-10-quantal)
[http://askubuntu.com/questions/226263/blank-desktop-after-installing-amd-driver-on-ubuntu-12-10](http://askubuntu.com/questions/226263/blank-desktop-after-installing-amd-driver-on-ubuntu-12-10)
[http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working](http://askubuntu.com/questions/205112/ubuntu-12-10-amd-intel-hybrid-graphics-not-working)

---

### Post by TheJeanValjean on 2013-01-02
Hello! Thanks for the speedy reply.  I have tried your method and it didn't work, after installing the drivers I restarted and it would not boot, giving me the error that said my computer was in low resolution.  In order to solve this I undid everything and am back to where I originally started.  Additionally, I have already tried all of the extra posts that you included.  Seriously, thanks for your time though I'm mad that this isn't working. Is there any other method that can get this thing to work or am I just doing something wrong?

---

### Post by TheJeanValjean on 2013-01-02
Ok so quick update, I did something and now my driver reads "Gallium 0.4 on llvmpipe (LLVM 0x301)" and my computer is running pretty slow.

---

### Post by LinuxDomi on 2013-01-03
> **TheJeanValjean said:**
> Ok so quick update, I did something and now my driver reads "Gallium 0.4 on llvmpipe (LLVM 0x301)" and my computer is running pretty slow.

Try this to solve the gallium problem:

[http://askubuntu.com/questions/183305/graphics-driver-being-reported-as-gallium-0-4-on-llvmpipe-llvm-0x300-instead-o](http://askubuntu.com/questions/183305/graphics-driver-being-reported-as-gallium-0-4-on-llvmpipe-llvm-0x300-instead-o)

There seems to be a solution for hybrid graphics on this forum:

[http://ubuntuforums.org/showthread.php?t=1930450](http://ubuntuforums.org/showthread.php?t=1930450)
[http://ubuntuforums.org/showthread.php?t=2083181&highlight=hybrid+graphics+amd+intel](http://ubuntuforums.org/showthread.php?t=2083181&highlight=hybrid+graphics+amd+intel)

But hybrid graphics seems to still be quite a problem...

Perhaps try to install only the AMD drivers:

```
sudo add-apt-repository ppa:andrikos
sudo apt-get update
sudo apt-get install fglrx
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

Be sure to search on the internet because others had this problem also and be sure to do the tutorials properly.

If nothing helps you can always put a live cd in and erase the ubuntu 12.10 partition and install ubuntu 12.04 LTS on it, of course assuming you have it on a seperate partition from your data...

---

