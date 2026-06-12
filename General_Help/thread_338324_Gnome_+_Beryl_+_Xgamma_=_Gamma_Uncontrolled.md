---
title: "Gnome + Beryl + Xgamma = Gamma Uncontrolled"
date: 2007-01-14
forum: General Help
---

### Post by Lu1s on 2007-01-14
I have an ati 9800pro using beryl, but a i got a monitor with some issues(everything seems darkness), before i installed my precious beryl i used the command xgamma to fix this problem, but now, when i use this command i get this:

kazekage@kazekage-desktop:~$ xgamma -gamma 1.5
Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".
Unable to query video extension version

any idea of could it be?, if i cant use the xgamma command then someone please try to recommend me a tool to control the brightness and the gamma correction, because i tried installed some of the synaptic but those tools didnt work. By the way, im using Gnome.

Any help will be more than welcome.

Luis Arias Jaen

---

### Post by Waappu on 2007-01-14
Hi

Have you installed ATI proprietary "fglrx" driver ? I think there is tool for that to adjust gamma. But I prefer to use open source drivers and then command xgamma probably works

---

### Post by Lu1s on 2007-01-14
indeed, i already installed the flgrx drivers but i dont know wich are & how to use, the command line tools of this drivers

---

### Post by Waappu on 2007-01-14
Hi

Have you installed fglrx-control? That should be tool for adjusting some properties for fglrx driver. It should be starting with this command
```
fglrx-control
```

---

### Post by Lu1s on 2007-01-14
> **Waappu said:**
> Hi

Have you installed fglrx-control? That should be tool for adjusting some properties for fglrx driver. It should be starting with this command
```
fglrx-control
```

Well, i got those drivers installed but that command dont work on my terminal :-?

---

### Post by Waappu on 2007-01-14
Hi

You need install that first

```
sudo aptitude install fglrx-control
```

---

### Post by Lu1s on 2007-01-14
well, i install them i got this message

kazekage@kazekage-desktop:~$ sudo aptitude install fglrx-control
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

but i tried to use the fglrx-control i got this message

kazekage@kazekage-desktop:~$ fglrx-control
bash: fglrx-control: command not found

---

### Post by Waappu on 2007-01-14
Hi

Sorry I can't remember what is command to start that ATI control panel. Try search from google

---

### Post by Waappu on 2007-01-14
Hi

Could command to launch ATI control panel be this ?```
fireglcontrol
```

---

### Post by Lu1s on 2007-01-14
yes i can but i got this message

and the panel itself shows this

---

### Post by Waappu on 2007-01-14
Hi

Have you modify /etc/X11/xorg.conf to use fglrx driver? I use open source driver and I don't have knowledge of fglrx drivers, sorry.

---

### Post by ontledroit on 2007-10-25
I have the same problem with an nvidia card.

philippe@eponyme:~$ xgamma
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Unable to query video extension version

using xserver-xgl package with compiz (ubuntu 7.10 x86_64)

Others programs (eg vmware player 2) complain for missing extension, although the package is present.

We should try harder.

---

### Post by Friedel on 2007-11-07
Hi there,

try ```
DISPLAY=:0 xgamma -gamma 1.0
```

1.0 = whatever you want

---

