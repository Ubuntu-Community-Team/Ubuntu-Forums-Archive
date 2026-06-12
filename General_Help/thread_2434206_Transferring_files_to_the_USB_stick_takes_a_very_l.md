---
title: "Transferring files to the USB stick takes a very long time as with Windows"
date: 2020-01-01
forum: General Help
---

### Post by besi1 on 2020-01-01
Hello, whenever files are copied on the USB stick, the system takes a long time to copy the files over. No matter how big the files are. I tried other USB sticks but the same problem. Egall wleche Ubuntu version I have the problem again. But who I copy over with Windows files I have no problems. Wiso is the problem only with Linux. Sometimes the system hangs up for a short while when copying over?

---

### Post by ajgreeny on 2020-01-01
How are you copying the files; using the file-manager or terminal ***cp*** command?
To give us as much info as possible, if you're using the file-mnager, try copying with a terminal command to see if that is any speedier.cp

---

### Post by Yellow Pasque on 2020-01-01
To show a little more info on the USB devices (with USB stick connected), run:
```
sudo lshw -C bus
sudo lsusb
```

---

### Post by HermanAB on 2020-01-03
There is a bug regarding specific hardware that has been in the USb stack for many a year.  

You should try ionice.  It may help:
$ sudo ionice cp fromfile tofile

---

