---
title: "New installation and &quot;MONITOR OUT OF RANGE&quot; ."
date: 2007-01-25
forum: General Help
---

### Post by Moloko on 2007-01-25
Hi all, I changed my video card and decided to perform a "clean" installation of Kubuntu 6.10. The card is a nVdia GeForce 6200A. I used the "alternate CD" for the installation without problems, but when KDE starts the monitor, a Sony CPD-E430, become black and appear a message:
```

MONITOR IS WORKING
**INPUT   : 200.0kHZ/300Hz**
OUT OF SCAN RANGE
CHANGE SIGNAL TIMING

```

After this I boot in text mode an type this command that I read in this forum:

```
sudo dpkg-reconfigure xserver-xorg
```

In the monitor section I selected the "Medium" option, 1280*1024@85Hz, and now the monitor show this message and hungs the PC again:

```

MONITOR IS WORKING
**INPUT   : 135.0kHZ/300Hz**
OUT OF SCAN RANGE
CHANGE SIGNAL TIMING

```

I didn't found where to change the 300Hz in the xorg.conf file, I think that my monitor doesn't support 300Hz.
Any idea ???  ....  Thanks in advance.

---

### Post by willcox on 2007-01-25
Hi!
Ok,  it was a deep nightmare for me too,  and it seems we have the same (and excellent!) dinosaur monitor.
code:
  sudo gedit /etc/X11/xorg.conf
Please,  see in the section Monitor,  and simply, copy & paste my section as:

Section "Monitor"

 ### Comment all HorizSync and VertSync values to use DDC:
    Identifier     "SONY CPD-E40"
    DisplaySize     370    270
    HorizSync       30.0 - 96.0
    VertRefresh     48.0 - 120.0
    Option         "DPMS"
EndSection

Sorry, I could not guaranteed success, but it would be the very first step.  Besides, you need this info pasted in your X11, BEFORE you proceed with the Nvidia drivers.
See you!

---

### Post by Moloko on 2007-01-25
Thanks for your help **willcox**, after add the lines you said to the xorg.conf file and  install the nVidia drivers a have the X windows up and  running ... :D 

Now I should tune the configuration, I don't get more than 85Hz using 1280x1024 , and I think that  our monitor supports 100Hz ... in other hand if I run **glxgears -printfps **the new card obtain similar results that the old and slow ATi Radeon 9250 using de free  driver  :confused: 

Thanks again ... regards.

---

