---
title: "Problems with binary nvidia driver"
date: 2007-12-14
forum: General Help
---

### Post by irotas on 2007-12-14
I'm trying to install the binary nvidia driver for my Dell Latitude c840 laptop, which has an Geforce 4 440 Go video card.

I found a thread on these forums where someone had luck with the 'Envy' script, so I decided to give it a shot. I ran it and it finished without any problems (it even modified my xorg.conf for me).

I reboot my computer, and then tried to 'startx', but the screen just goes black.

You can download my xorg configuration and log file here:
[http://irotas.fastmail.fm/xorg.conf](http://irotas.fastmail.fm/xorg.conf)
[http://irotas.fastmail.fm/Xorg.0.log](http://irotas.fastmail.fm/Xorg.0.log)

You can ignore the errors in the log file relating to my Synaptics Touchpad; that's an entirely separate issue, but not really a problem.

There are some suspicious warnings in the log file, but I'm not sure if they are related to this particular problem or not.

Also, I get the following from lspci:
01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go] (rev a3)

I think I'm close to getting this to work, but there's something I'm missing here. Anyone have a clue what may be wrong or how to troubleshoot this?

If it matters, I'm running Gutsy Gibbon.

Thanks,
Adam

---

### Post by irotas on 2007-12-14
I found a similar discussion to this problem here:
[http://www.fedoraforum.org/forum/showthread.php?p=672671](http://www.fedoraforum.org/forum/showthread.php?p=672671)

One of the repliers posted an xorg.conf that worked for him on a c840. To mimic what he did, I added the following to my xorg.conf:
	Option	    "NoLogo" "True"
	Option	    "UseDisplayDevice" "DFP"
	Option	    "AddARGBGLXVisuals" "True"

Now X actually starts, but I get the exact same distortion mentioned here:

> **eimajenthat said:**
> About 1.5 inches on the right side is consumed by colored lines, and about 1.2 inches on the bottom is consumed a repeat of the top of the desktop.

Everything worked fine with NV, except for GLX.  I only changed the driver, and the line about using DFP (without that, I get a blank screen).


Any ideas?

---

### Post by PmDematagoda on 2007-12-14
Why didn't you try installing the Nvidia driver using the Restricted Drivers Manager? Usually that is what people do first in order to install the necessary drivers before going down the other methods.

The Restricted Drivers Manager can be found in System>Administration>Restricted Drivers Manager.

---

### Post by irotas on 2007-12-14
> **PmDematagoda said:**
> Why didn't you try installing the Nvidia driver using the Restricted Drivers Manager? Usually that is what people do first in order to install the necessary drivers before going down the other methods.

The Restricted Drivers Manager can be found in System>Administration>Restricted Drivers Manager.


I just installed the Restricted Drivers Manager and tried it out for enabling the 'nvidia' driver. However, now when I try to start X, my screen just goes black.

---

### Post by PmDematagoda on 2007-12-14
Do:-
```

sudo dpkg-reconfigure xserver-xorg
```
And select the driver as Nvidia and any other options you may want, after that is done, try:-

```
sudo startx
```

---

### Post by irotas on 2007-12-14
> **PmDematagoda said:**
> Do:-
```

sudo dpkg-reconfigure xserver-xorg
```
And select the driver as Nvidia and any other options you may want, after that is done, try:-

```
sudo startx
```



Of course, I've tried this several times over with a variety of options. Regardless of whether I auto-generate my xorg.conf or set it up manually, I get the same problem when I switch to the 'nvidia' driver - a blank screen.

With those 3 options I mentioned before, I can get past the blank screen, but I have the same visual distortion as was described by the guy I quoted.

Thanks,
Adam

---

### Post by PmDematagoda on 2007-12-14
Could you post what version of Ubuntu you use?

---

### Post by irotas on 2007-12-14
> **PmDematagoda said:**
> Could you post what version of Ubuntu you use?

Gutsy Gibbon 7.10

---

### Post by PmDematagoda on 2007-12-14
Ok, try installing the Nvidia drivers manually by following these steps:-

1) Download the Nvidia driver for Linux from [here]("http://www.nvidia.com/object/unix.html").

2) After that is done kill the GUI using:-

```
sudo /etc/init.d/gdm stop
```

3) Navigate to where the Nvidia driver installer is located and run it using:-

```
sudo sh nameofinstaller
```

4) After that is done do:-

```
sudo dpkg-reconfigure xserver-xorg
```

5) After configuration is done do:-

```
sudo /etc/init.d/gdm start
```
to start the GUI.

---

### Post by irotas on 2007-12-16
Found a solution!

[http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26](http://www.nvnews.net/vbulletin/showpost.php?p=1068062&postcount=26)

---

