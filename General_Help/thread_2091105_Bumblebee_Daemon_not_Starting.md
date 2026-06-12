---
title: "Bumblebee Daemon not Starting"
date: 2012-12-04
forum: General Help
---

### Post by Martom on 2012-12-04
Hello all,

I have a GeForce GT525M in my new laptop and under Xubuntu 12.10 I seem to be afflicted with the problem described in this thread:

[http://ubuntuforums.org/showthread.php?t=2075423](http://ubuntuforums.org/showthread.php?t=2075423)

However, I am not having any luck getting this solved as Bumblebee is not working for me. Now, I also saw the various threads about having to install the kernel headers manually, but this also does not seem to be my problem as they were already installed:

```
:~$ sudo apt-get install linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.5.0-19-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```After installing Bumblebee, I am now stuck on a lower resolution and optirun gives me the error

```
:~$ optirun glxspheres
[  793.097174] [ERROR]The Bumblebee daemon has not been started yet or the socket path /var/run/bumblebee.socket was incorrect.
[  793.097193] [ERROR]Could not connect to bumblebee daemon - is it running?

```Even if I manually start Bumblebee, I get the same error. What else can I do to troubleshoot this? Should I have installed Bumblebee in the first place? I was able to use maximum resolution before I did.

Cheers.

---

