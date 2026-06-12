---
title: "about ubantu13.10 webcam not working .."
date: 2013-10-23
forum: General Help
---

### Post by paritosh-surve on 2013-10-23
hello everyone i have just installed ubantu 13.10 64 bit on my DELL studio 14 laptop but since my webcam is not working anymore.
plz provide solution.
might be driver problem

---

### Post by varunendra on 2013-10-25
Welcome to the forums Paritosh !

Please open a terminal (Ctrl-Alt-T) and post back the outputs of the following commands -
```
lsusb
usb-devices
cat /proc/bus/input/devices
lsmod
```

And which application(s) are you using with the webcam? My personal recommendation is "guvcview" for offline webcam booth.

---

