---
title: "URGENT! fsck and boot problem"
date: 2008-02-19
forum: General Help
---

### Post by jorgecarrillo150990 on 2008-02-19
So i started browsing on the internet to get a way to stop the "sda3 has been mounted 28 times without checking, check forced". And I ran across a command called "fsck" I didn´t knew what to do, but according to other problems it worked perfectly.

So I ran the terminal and typed "fsck", it gave me a warning, but still followed.
It ran some stuff in the screen, like checking. And after that there was no problem, until I tried to refresh a website in Firefox and a popup said that I didn't have enough space.

So I reboot my laptop and when I went to the Ubuntu splash screen, it turned black and letters started appearing, I think it was doing the boot in the terminal.

After that a blue screen appears saying something about the GDM, it said I had to do something and then reboot.

There was a button which said "OK", so I clicked it and again the terminal boot appeared.
It asked me for my login and password.
And went directly into the terminal.

Maybe I did something innapropiate, I dont know.
But I want my Ubuntu back.

PS. If there is no soltion can you tell me a way to make a backup CD from terminal, a way to eliminate Gutsy and make a new clean install?

---

### Post by chrisccoulson on 2008-02-19
If you are getting to a terminal, try:
```
sudo dpkg-reconfigure xserver-xorg
```

The warning you got when running fsck was probably the one that tells you it is very dangerous to run fsck on a mounted filesystem, and you shouldn't have ignored the warning really. Always unmount before running fsck.

If you want to disable or alter the frequency of automatic filesystem checking, I suggest you check out tune2fs
```
man tune2fs
```
..particularly the -c and -i options. I wouldn't recommend totally disabling all forms of auto-checking, as it may save your data in the event of hardware faults creeping in.

---

### Post by jorgecarrillo150990 on 2008-02-19
It didnt work...
I put in the terminal
```
sudo dpkg-reconfigure xserver-xorg
```

But nothing happened, it only appeared:

```
dpkg-query: failed to open /var/lib/dpkg/status/
```
```
xsever-xorg is not installed
```

If you dont know whats going on please tell me how to make a backup of my HOME folder and how to eliminate Gutsy to make a clean install.

---

### Post by jorgecarrillo150990 on 2008-02-19
I need serious help here, please.

---

### Post by pointone on 2008-02-19
Running fsck on a mounted partition usually corrupts a lot of the data on it. I'm not sure how you could go about recovering from this besides a reinstall. You should perhaps wait for someone with more fsck recovery experience than I before continuing.

Nonetheless, to backup and reinstall, all you need is an Ubuntu disk. Boot into the live CD environment and you'll be able to access your local drive. Hopefully nothing in your home is corrupted, and you can easily copy it to another partition / network share. After everything is backed up, simply run the installer from the live CD and it should overwrite the same partition you previously installed on.

---

### Post by jorgecarrillo150990 on 2008-02-19
Thank you, I will do that...I hope this never happens again...

---

