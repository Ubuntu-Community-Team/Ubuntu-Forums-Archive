---
title: "Poor scrolling performance after a while"
date: 2007-03-24
forum: General Help
---

### Post by tthkbw on 2007-03-24
I am running Ubuntu 6.10 on Dual Pentium 820 with 1.5GBytes of ram.  Video is Motherboard based ATI Radeon Xpress 200.

Everything works pretty well, but after being logged in for a while (sometimes a few minutes, sometimes a few hours) and doing stuff, The scrolling performance in gvim or console vim becomes very slow (doesn't come close to keeping up with the keyboard repeat rate.  When the slowdown is occurring, htop shows that X is taking 99% of the cpu.

If I then log out and log back in, scrolling performance is excellent, and while scrolling, X takes only up to about 30% of the cpu.

I haven't yet been able to tie this slowdown to anything I am doing.  

Any ideas?

Terry Brown
Stickman Software
[http://stickmansoftware.com](http://stickmansoftware.com)

---

### Post by tthkbw on 2007-03-29
So nobody but me cares.  I can live with that.  

I have solved the problem, and, not surprisingly, it was video drivers.  Although I had installed the ATI drivers, the install didn't really quite take.  In xorg.conf, the driver was listed as "ati".  After wading through a bunch of HOWTOs and such found through Google, something I did changed this to "fglrx", and then things got lots better.  I believe this involved at least one reinstall of the ati drivers, and I know it involved creating some links by hand.  But after that, the scrolling problem appears to have disappeared and the performance of firefox scrolling is much better as well.  

One comment:  There's no way an unsophisticated user could ever figure this kind of stuff out.  They'd just think Linux performance sucked--Windows is much better.  Although Ubuntu did "just work" out of the box, and I have been mightily impressed with my ability to easily get printing (on a Windows networked printer) and usb stuff to work (including a wireless usb dongle that is technically unsupported under Linux), the basic video driver problem on off the shelf hardware (a Compaq 2044NX) is really disappointing.  And I am obviously not alone--based on what I have read, I'm just glad I don't have Nvidia hardware.

I still haven't solved another problem--I still don't have 3D acceleration.  I may try Envy to install the ati drivers to see if that works better--but not until I decide how to image by hard drive so that when I screw it all up and it doesn't even boot any longer, I can recover.

By the way, I am committed to Ubuntu replacing my windows XP installation--although I do run the original Windows from my hard drive using vmware player.  And I have convinced the folks at work to use Ubuntu for our Linux desktops.  At work, although getting things like NFS server to work have been challenging, its a lot easier than Red Hat ever was.

---

### Post by kc0eks on 2007-04-02
I see nearly the same problem as you, I posted in another thread about this, however I havent got very far. My xorg shows fglrx and scrolling just sucks. unless i reboot quite frequently. 
When I scroll CPU usage goes up to 99% and just lags like no other..

---

