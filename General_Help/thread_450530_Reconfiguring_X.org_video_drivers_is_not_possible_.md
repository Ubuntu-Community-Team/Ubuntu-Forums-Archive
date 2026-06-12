---
title: "Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid"
date: 2007-05-21
forum: General Help
---

### Post by paroa on 2007-05-21
Hello, I need som help after I tried to configur my mouse. I have replaced my xorg.conf with xorg.conf.backup, but I think I did somthing wrong. It seems that the nvidia driver dosen't work because when i write gksudo nvidia-settings in terminal I get this back: 

(gksudo:6011): Gtk-WARNING **: Failed to set text from markup due to error parsing markup
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':0.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':0.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':0.0'.

If I write  sudo gedit /etc/X11/xorg.conf in terminal i only get's a blank sheet.

---

### Post by taurus on 2007-05-21
1.  The command should be

```
**sudo** nvidia-settings
```

2.  And if you need to edit /etc/X11/xorg.conf, then it should be

```
**gksudo** gedit /etc/X11/xorg.conf
```
And if you moved your xorg.conf to xorg.conf.backup, then move it back.

```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```

---

### Post by dexter on 2007-05-21
If you really messed up xorg.conf and fail to get your backup working, you can reconfigure xorg using
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by paroa on 2007-05-21
Thank you very much Dexter, it works perfectly! Taurus, No one of your suggestions worked, I just got the same errors. But thanks for your help both of you!

---

### Post by paroa on 2007-05-21
One more problem, I cant find my projector in nvidia x settings any more. Any ideas how to get it back?

---

