---
title: "[Lubuntu] Native linux game no longer working after update from artful to bionic"
date: 2018-07-20
forum: General Help
---

### Post by ivoid on 2018-07-20
I used to play Super Crate Box just fine before the update, now I get this error:
```
error while loading shared libraries: libcrypto.so.1.0.0: cannot open shared object file: No such file or directory
```
I found that the file libcrypto.so.1.0.0 is part of the package "libssl1.0.0", and I've verified that I have it installed and updated, still doesn't work.

Anyone have any ideas?

Thanks in advance.

---

### Post by Dennis N on 2018-07-20
> I used to play Super Crate Box just fine before the update, now I get this error:
This is a game that was installed in 17.10 and is still the original install of the game?

---

### Post by Dennis N on 2018-07-20
Assuming your answer to post #2 is yes, I'll offer you the probable cause to save time:

The file location of that library has changed from:
```
/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
```
to:
```
/usr/lib/x86_64-linux-gnu/libcrypto.so.1.0.0
```
Your game is probably using the old location. You could put a copy of the file into the old location and see if that solves the problem.

---

### Post by ivoid on 2018-07-21
Thanks for the help.

I had the game on my HDD before the update to bionic, but the game was never installed per se, as it was downloaded as a simple zip archive, not a package.

Still, I followed your suggestion but there was no effect, same error.

---

### Post by ivoid on 2018-07-21
I got it to work! :D

I installed the 32bit version of libssl1.0.0 and now it works! (I'm running 64bit Lubuntu)

The error message is misleading though, the 32bit and 64bit versions of the file have exactly the same name and I had no way of knowing which one was missing.

---

### Post by Dennis N on 2018-07-21
Thanks for reporting back. My suggestion in post #3 was based on a 'yes' answer to post #2, i.e.,  that it was installed before in Lubuntu 1710. 

Yes, you need 32-bit libraries to run a 32-bit game. If you don't know what the architecture is,  use the **file** command on the executable. Example:
```
dmn@Sydney:/opt/aquaria$ file aquaria
aquaria: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), dynamically linked, interpreter /lib/ld-linux.so.2, for GNU/Linux 2.4.18, not stripped

```
Enjoy your game!

---

### Post by ivoid on 2018-07-21
Thank you! I'll remember to use the **file **command next time :)

BTW, I usually use the Synaptic package manager but for 32bit packages I had to use **apt **on the terminal, do you happen to know if I can manage 32bit packages with Synaptic or if there is another more complete package manager?

---

### Post by Dennis N on 2018-07-21
> **ivoid said:**
> Thank you! I'll remember to use the **file **command next time :) BTW, I usually use the Synaptic package manager but for 32bit packages I had to use **apt **on the terminal, do you happen to know if I can manage 32bit packages with Synaptic or if there is another more complete package manager?

Yes you can use Synaptic. Notice the 'Architecture' button on the lower left side. Press it, then select "arch: i386" in the small window in upper left. To find a package so you can install it, click in the package list and start typing the name you want, and it searches as you type.  

Note: The regular 'Search Tool' in the tool bar seems to only find 64-bit packages, so that seems broken now for 32-bit. 

Image attached: find 32-bit package libXcursor1

---

### Post by ivoid on 2018-07-22
Yes! That's what's been happening to me, I was using the 'Search Tool' and only got 64bit packages, now I understand. Thank you so much, you've been really helpful.

---

