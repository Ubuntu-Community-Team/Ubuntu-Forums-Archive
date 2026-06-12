---
title: "help with xgl removal and restricted driver activations"
date: 2008-02-27
forum: General Help
---

### Post by AMM6 on 2008-02-27
my desktop effect would not turn on so i was told to intstal xgl however no i cant even log in outside of gnome failsafe please send instructions on how to remove xgl.    I am running a trident blade 3d graphics card(looking for a better one) and i cannot activate any graphics drivers.  Driveres worked fine when i had windows.  hope its my fault not ubuntu

---

### Post by AMM6 on 2008-02-27
plz answer quickly failsafe is realy slow

---

### Post by Rocket2DMn on 2008-02-27
From the terminal run
```
sudo apt-get remove *packagename*
```
where *packagename* is the name of the xgl package you installed (xserver-xgl?)
You can then reconfigure X with
```
sudo dpkg-reconfigure -phigh xserver-xorg
```  Then restart the computer into normal mode (or if you are already in the regular kernel, do CTRL+ALT+BACKSPACE).

If you want to configure X manually, follow this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

If you need more help, reply with the output of these commands:
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

