---
title: "nVidia driver"
date: 2013-02-16
forum: General Help
---

### Post by linuxsyst on 2013-02-16
Hello, so I tried finding some drivers for my video card but I can't find the correct one I tried installing a lot of them and when I download the one from nvidia it gives me an error, now I have this ```
root@blackhat:~# glxinfo | grep -i vendor
server glx vendor string: SGI
client glx vendor string: Mesa Project and SGI
OpenGL vendor string: VMware, Inc.

```

Please help :confused:

---

### Post by Yellow Pasque on 2013-02-16
Please show output of
```
lspci | grep VGA
```

---

### Post by linuxsyst on 2013-02-16
```
01:00.0 VGA compatible controller: NVIDIA Corporation G71 [GeForce 7900 GS] (rev a1)

```

---

### Post by Frogs Hair on 2013-02-16
Check Additional Drivers for available drivers if you haven't already.

---

### Post by linuxsyst on 2013-02-16
I did... Here is the screenshot: [IMG]https://dl.dropbox.com/u/24275350/Screenshot%20from%202013-02-16%2022%3A12%3A16.png[/IMG]

---

### Post by Frogs Hair on 2013-02-16
I am using the Experimental Nvidia binary Xorg driver on my 8 series Nvidia card. I am on 12.10 and the driver descriptions are much better. I am also running a different Kernel.

---

