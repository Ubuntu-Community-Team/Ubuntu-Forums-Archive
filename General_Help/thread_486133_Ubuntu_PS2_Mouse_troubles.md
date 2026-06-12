---
title: "Ubuntu PS/2 Mouse troubles"
date: 2007-06-27
forum: General Help
---

### Post by kungfugecko on 2007-06-27
Howdy,

This is my first venture into the land of Linux, and it's getting a touch rocky.

A few days ago I installed Ubuntu for the first time, and haven't had any problems with it since then. Everything is working great on that machine. Yesterday, I decided to throw it on another machine, which was running Windows 2000, to see how it would work with the slightly-more outdated hardware. The install went perfect, however the PS/2 mouse doesn't seem to be working. It loads up to the login screen, I can see the cursor in the middle, but it isn't moving at all, and I can't click either. The mouse works fine, I just used it on a different computer to test it, and the PS/2 port on the computer works fine too. I've google'd for a couple hours now, looking for a solution, and have tried several things but nothing worked.

I tried the solutions mentioned here [http://ubuntuforums.org/showthread.p...ht=bodzasfanta](http://ubuntuforums.org/showthread.p...ht=bodzasfanta)
to no avail.

I also tried someone's suggestion of

sudo apt-get install mdetect

after it downloaded and installed, I ran

mdetect

and get this

ben@ubuntu:~$

(it just goes back to the command prompt)

Also, I just tried to run Ubuntu as a live CD, and the mouse didn't work then either.

If anyone has any suggestions on how to fix this problem, I would greatly appreciate it!

Thanks!

*originally posted here [http://ubuntuforums.org/showthread.php?t=486003](http://ubuntuforums.org/showthread.php?t=486003), but I believe this is the correct sub-forum for this post*

---

### Post by kungfugecko on 2007-06-27
I've found a relevant post which may help this problem, hopefully someone can tell me what it means >_<

from [https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221](https://bugs.launchpad.net/baltix/+source/linux-source-2.6.20/+bug/108221)

"I have put a test kernel in [http://people.ubuntu.com/~pkl/ps2](http://people.ubuntu.com/~pkl/ps2). This kernel has a number of patches which may fix this problem. There is currently a kernel for i386, a x86_64 kernel will be available as soon as it builds.

Please test and let me know if this test kernel fixes the ps/2 mouse/keyboard problem.

If anyone needs to know, the package can be installed by sudo dpkg --install linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb and removed by sudo dpkg --purge linux-image-2.6.20-16-generic (for the i386 version).

Thanks"

another person says:

"This bug fix is now available as an official Ubuntu update.

Thanks to everyone who tried the test kernel, and reported their experiences. I'm marking this bug as fixed."


I tried the "sudo dpkg --install linux-image-2.6.20-16-generic_2.6.20-16.28_i386.deb" that he suggests, but it says the package cannot be found.  There is a link to download it here [http://people.ubuntu.com/~pkl/ps2/](http://people.ubuntu.com/~pkl/ps2/)
however I don't have any idea how to download/install it from a command line in linux.  If someone could post some advice I would appreciate it.

Thanks!

---

### Post by loserboy on 2007-06-27
does that computer have a SiS chipset?

also it looks like a fix has been released through the updater so all you woould have to do is have everything updated

---

