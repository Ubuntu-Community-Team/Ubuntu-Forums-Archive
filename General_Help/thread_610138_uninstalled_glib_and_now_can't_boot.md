---
title: "uninstalled glib and now can't boot"
date: 2007-11-11
forum: General Help
---

### Post by rob1101 on 2007-11-11
well the short version is i downloaded the newest glib and tried to install it (./configure, make, sudo make install ) but it didnt do what i needed it to do. so i  tyried again with (  ./configure --prefix=/usr , make, sudo make install user ) still didnt do what i needed it do do so i gave up. then when i rebooted my machine later i find that it wont boot into ubuntu i get this message. 

```

Starting up...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/*"bunch of numbers and letters here")* = s
da5(8,5)
kint: trying to resume from /dev/disk/by-uuid/"[I]more numbers and letters here"
[/I]kinit: No resume image, doing normal boot...

Ubuntu 7.10 robert-desktop tty1

robert-deskto login: _

```and thats it i can login and still have the shell but i dont know how to fix it. 
i cd to the /usr/bin and the glib directory is gone but the glib-config file is there. i still have the files i need to install the newer version of glib but you see how well that went. 

what do i do?

---

### Post by oldos2er on 2007-11-11
Try running 'startx' after you login. Does anything happen?

---

### Post by rob1101 on 2007-11-11
yes it acts like it wanst to boot up, the screen flashes i see a cursor then it goes back to the promt with this message.

```

"[I]bunch of info about my system, and it tells me about some markers"
[/I](WW) = warning
(EE) = Error

(WW) fglrx: No matching Device section for instance (BusID PCI:1:0:1) found
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
(EE) AIGLX: reverting to software rendering
SetClientVersion: 0 9

waiting for X server to shut down FreeFontPath: FPE "/usr/share/fonts/X11/misc"
refcount is 2, should be 1; fixing.

```

---

### Post by oldos2er on 2007-11-11
Sorry, your problem's beyond my ability to help. The only other thing I can think to do would be to run '[SIZE=-1][B]sudo dpkg-reconfigure xserver-xorg'

[/B][/SIZE]

---

### Post by rob1101 on 2007-11-12
> **oldos2er said:**
> Sorry, your problem's beyond my ability to help. The only other thing I can think to do would be to run '[SIZE=-1][B]sudo dpkg-reconfigure xserver-xorg'

[/B][/SIZE]

didn't work thanks for the help though.

---

### Post by rob1101 on 2007-11-13
anyone else got any ideas or do i have to reinstall :(

---

### Post by dadawan on 2007-11-13
I'm getting the same thing.  And so are other people:

[http://ubuntuforums.org/showthread.php?t=612398&highlight=FreeFontPath](http://ubuntuforums.org/showthread.php?t=612398&highlight=FreeFontPath)

[http://ubuntuforums.org/showthread.php?t=610203&highlight=FreeFontPath](http://ubuntuforums.org/showthread.php?t=610203&highlight=FreeFontPath)

  -Kevin

---

