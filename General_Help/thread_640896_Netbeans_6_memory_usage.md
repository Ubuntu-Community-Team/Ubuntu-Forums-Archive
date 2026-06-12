---
title: "Netbeans 6 memory usage"
date: 2007-12-14
forum: General Help
---

### Post by ghostlines on 2007-12-14
I run Ubuntu gutsy 64bit . I recently installed the latest netbeans version 6, and noticed that it's running slower than the previous version. I then checked my processes and noticed that the java process that netbeans uses is now pulling 407mb. I have a friend who is also running netbeans on Debian and he pulls about 169mb of ram.

This is without having any project running, just default after opening netbeans 6

Does anyone know why this is, and if i could solve this problem ?
Any help is appreciated.

---

### Post by phibit on 2008-01-23
I have the same problem!! Netbeans 6 appears to be a memory hog. I had the same symptom of Netbeans pulling over 400 MB of RAM, but I was able to alleviate the problem somewhat (down to "only" 295 MB) by going into Tools | Plugins and disabling some modules form loading on start up.

Still, 295 MB is an incredible amount of RAM for an IDE to use... Anybody else have any tips?

---

### Post by igor_mk on 2008-03-05
I have the same problem, NetBeans6 is taking more than 400mb ram. And in the netbeans.conf max memory is set to 200m... I'm using ubuntu 7.04 64bit. Anyone has an idea how to fix this?

thanks

---

### Post by valczir on 2008-04-11
I know this is a fairly old thread, but I wanted to reply on the off-chance that it helps someone else out.  Netbeans is currently my favorite IDE, and I don't wanna leave info out there that may dissuade people from using it.

I had the same problem on gentoo 64-bit, but the problem was no where near as bad on xubuntu 32-bit (I use xubuntu when I need to get things done fast, gentoo when I need things to work how I expect them to).  I haven't tried installing the 32-bit version of Netbeans 6 on my installation of gentoo, yet, but my guess is that the problem lies with the 64-bit version.  So my suggestion would be to run the 32-bit version either in a 32-bit chroot or on x86 emulation libraries.

---

