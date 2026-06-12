---
title: "[SOLVED] What is KDE's equivalent of gksu?"
date: 2007-08-13
forum: General Help
---

### Post by nirpius on 2007-08-13
Hi, I'm a KDE convert (purely because I like having a slideshow as my background and I prefer Amarok, Digikam and Kontact to Rhythmbox, F-Spot and Evolution). The only thing is, when using the command line just now and trying to run 'gksu kate' (text editor) it said gksu was uninstalled, I went to install it and found it depended on some Gnome libraries and I was just wondering if their was a KDE equivalent. I have heard of kdesu but it said it was a bad command when I tried it.

---

### Post by bluenova on 2007-08-13
kdesu is correct, did you do a standard kubuntu install?

---

### Post by nirpius on 2007-08-13
Yeah straight from the ISO which wasn't corrupted when I checked it. I checked Kate and it was working but I don't know how to get it to work in SU mode.

I tried:

```
kdesu kate
```

and got

```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

So I looked in the menu editor to find what the command for Kate was and then tried

```
kdesu kate --use %U
```

This gave me

```
kdesu: Unknown option '--use'.
kdesu: Use --help to get a list of available command line options.
```

---

### Post by ErusGuleilmus on 2007-08-13
```
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
```

The same thing shows up for me in the konsole, but the text file opens any way and I can edit it as if nothing happens. Does Kate still open for you even though this occurs?

---

### Post by miggols99 on 2007-08-13
There's nothing wrong with it. It is a harmless message. If you want to remove it, I think you have to remove some lines from your xorg.conf. Search around and you'll find it somewhere.

---

### Post by nirpius on 2007-08-13
It didn't before but this time it did, It hocked out all that Failed to Open Device Stuff about 3 times then opened. Maybe, I've just got a messy install...

Thanks anyway, problem solved

---

