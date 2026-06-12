---
title: "ATI compiz problems"
date: 2007-11-03
forum: General Help
---

### Post by capo327 on 2007-11-03
I followed the [guide]("http://ubuntuforums.org/showthread.php?t=591445&highlight=ati+compiz") for getting compiz to work on Gutsy with ATI, but it doesn't work.  When I try to enable compiz through the Appearances dialog box, it says 'Desktop effects could not be enabled.'  I tried starting it through the terminal, and here's the output I got:

```
javier@javier-linux:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:7280 (rev 9a) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 
```

---

### Post by Light- on 2007-11-03
heres your problem:

```

Checking for Xgl: not present.

```

try installing xserver-xgl and all should be well (im assuming your using the fglrx driver)

---

### Post by capo327 on 2007-11-03
I installed it, and when I logged back in, the screen was just a blank, so i had to logout and remove xgl via the terminal.

---

### Post by strabes on 2007-11-03
Paste the output of this command:```
fglrxinfo
```

Light: Please don't tell people to install xserver-xgl unless you tell them the risks associated. (extreme instability, slow performance, no glx, etc.)

---

### Post by capo327 on 2007-11-03
```
fglrxinfo: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

---

### Post by Light- on 2007-11-03
> **strabes said:**
> Paste the output of this command:```
fglrxinfo
```

Light: Please don't tell people to install xserver-xgl unless you tell them the risks associated. (extreme instability, slow performance, no glx, etc.)

Sorry, i was under the impression it was required for getting Compiz to work with the proprietry ati driver from the ubuntu repos.

also, ive never had any problems with it regarding stability/performance, it worked fine when I had it enabled (disabled now as I traded having Compiz one display for having two displays at native resolutions)

---

### Post by atrapine on 2007-11-04
had a similar problem with a Radeon9600? After loads of playing around found it is a fault with the new ATI drivers under Gutsy.
The best way is to Use envy and download the earlier version of the ati drivers and you should be good to go.

---

