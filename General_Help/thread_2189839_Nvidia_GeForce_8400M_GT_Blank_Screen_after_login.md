---
title: "Nvidia GeForce 8400M GT: Blank Screen after login"
date: 2013-11-24
forum: General Help
---

### Post by colder111 on 2013-11-24
Hey all,  

I've looked all over the web for a solution for this, with no luck, hope someone here can help.  

I have a desktop and a laptop which until recently,  both ran 12.04 32-bit with nvidia proprietary drivers. No issues, everything ran fine. I decided to install 13.10 64-bit.  Desktop worked fine. I did not even bother installing nvidia as nouveau worked great (lost of resolution choices, crisp image etc)  


Laptop was another story. As soon as I was done with the installation, everything moved in "slow motion", hovering the mouse over the menu bar for example, it takes a full two seconds to show the name (e.g. open firefox) and I would see the label slowly fading in. Application windows open in the same manner, very slowly fading in and fading out on close. Only two resolution choices, 1024x768 and 800x600. So I decided to intall the proprietary driver from additional hardware. A bunch of choices (319,304,304-updates etc), I tried each one with the exact same results:  


While booting, the logo disappears and "Ubuntu 13.10" shows in its place. Then the login menu displays just fine. I log in, and then blank screen. I can only see the mouse moving.  Hit Alt-Ctrl-F1, log in, and type "unity". I go back to graphic, (Alt-Ctrl-F7), still nothing but if I hit Alt-Ctrl-T a terminal now opens. I type nvidia-settings and I get an error message that nvidia drivers are not in use. 

Back on the other terminal where I typed "unity", I see an error failed to load "nvidia_319" or 304 or all other I tried.  I have tried nvidia-xconfig and a bunch of other tweaks in xorg.conf, no luck. Only if I delete all nvidia can I revert to a normal desktop (with nouveau), but then it feels like I'm using a 20-year old laptop with brand new software, as I described above.  Laptop is a Sony Vaio AR-825E with nvidia GeForce 8400M GT.  

Any help appreciated.

---

### Post by colder111 on 2013-11-24
Btw,

I forgot to mention I also tried installing Fedora 19 64-bit, and I had the same experience-slow graphics. I did not try to install proprietary drivers with Fedora though, I just removed and re-installed Ubuntu.

---

### Post by colder111 on 2013-11-24
UPDATE:

I am not sure, but I think the problem may lie either with the 64-bit version, or the newer kernels.

I installed 12.04 64-bit (I had 12.04 32-bit before). I did the updates after install, and then system would not boot to the updated kernel (3.8.0.33), the num lock/caps lock would blink and screen blank right after grub selection. The previous kernel worked though (3.8.0.29). I installed all nvidia drivers again, same issues as described in the first post.

To verify I am not insane, I downloaded 12.04 32-bit that I had before all this mess, installed it and everything works perfectly. Both the nvidia drivers and booting to 3.8.0.33. Maybe 13.10 32-bit might work as well, but after an entire day I am just tired to keep working on this, and I need the laptop to work on, so I may try it at a later time...

---

### Post by melkyades on 2014-02-26
I've had this problem since ever. My GeForce 8400M won't run any ubuntu 64 bits (12.04/12.10/13.04/13.10) without crashing or freezing. With nouveau the screen gets corrupted after some usage until the system crashes. I've tried most kernels since 3.2 in ubuntu 12.04. With nvidia blob the system freezes at login. Ubuntu 12.04 32-bits works well at least.

---

### Post by jeanjd63 on 2014-02-26
Hello

You can try these commands :
[B]sudo  apt-get  purge  "nvidia *"
sudo  apt-get  install  nvidia-current[/B]
and
**sudo  reboot**

---

### Post by melkyades on 2014-04-18
After years (literally!) waiting, users of nVidia GeForce 8400m (and G86M family) can celebrate. The issue seems to be fixed with nvidia-331 drivers. What is even better, the corruption bug with this GPU when using nouveau was [found and fixed]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1158689") in Kernel 3.14, so both nouveau and binary blobs are working finally. I've tested this in the just released Ubuntu 14.04 64-bits (ships with kernel 3.13 but I updated to 3.14.1). Cheers!

---

### Post by sam28 on 2014-04-24
I have also same problem with drivers (here is my [topic]("http://ubuntuforums.org/showthread.php?t=2205163&highlight=nvidia+8400m")). So now i should install ubuntustudio 14.04 + download nvidia drivers 331 (latest stable is 331.67) from official website and all b fine?

---

### Post by luctor on 2014-04-28
Can't wait to test this !!!
I'll report soon

---

### Post by luctor on 2014-04-29
Installed the drivers in lubuntu 14.04 on my 8300GS which had exactly the same problems as the 8400gm.
They work **GREAT**! Have used them for one day; 3d games, compositing, wine. No problems so far

---

