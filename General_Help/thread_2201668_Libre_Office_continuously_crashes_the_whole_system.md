---
title: "Libre Office continuously crashes the whole system"
date: 2014-01-25
forum: General Help
---

### Post by DrScum on 2014-01-25
I did a clean install of Ubuntu 12.04 LTS on a Dell Inspiron 6400 Laptop, did all the updates and have only Ubuntu packages installed, nothing out of the ordinary. Libre office keeps crashing the system when there are multiple documents open and I want to access them via the unity launcher. With crashing the whole system I mean nothing is available anymore, just the mouse pointer the only way out I found is cut the power!

Before I used a Vostro1520 system, the display broke,  which also had 12.04 LTS but with Gnome fallback, Docky and Libre Office 4.1 from the Libre Office repositories. With that system I didn't have these problems. 

My Question: are the problems caused by the somewhat older machine, by the fact that Unity and Libre Office don't work together well or do you recommend to install Libre Office 4.1?

---

### Post by grahammechanical on 2014-01-25
In all my experience of using Ubuntu since 2007 I have never found any incompatibility between Ubuntu and Libreoffice. Not since Libreoffice was used to replace Openoffice. I am now using the Latest Ubuntu (Trusty Tahr) with the latest Libreoffice (4.1.3) and there is no conflict. It sounds like Unity is crashing or may be Compiz - the window/compositing manager. It may even be a problem with the video driver.

We can usually get to a terminal through Ctrl+Alt+T or Ctrl+Alt+F2 or another F number. In a terminal we can run

```
sudo shutdown -r now
```

to restart. Or

```
sudo shutdown -h now
```

to shutdown.

If we have lost the Launcher and the top panel we can right click the desktop and select Change Desktop Background. That will open System Settings. From there we can use Additional Drivers to experiment with video drivers. We will need to reboot to see if the new driver works.

Does this crash occur with other applications? What video adapter does the machine have and how much video memory does it have? I looked at one review which said Ati Mobility Radeon X1400 256MB memory. That I think is the barest minimum for Ubuntu + Unity.

Regards

---

### Post by DrScum on 2014-01-26
Thanks for the response. Here some answers to questions you asked:
lspci | grep vga output:
Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
couldn't get any more information about the memory, but since it's integrated I guess its sharing the main memory

Other apps didn't crash so far but that's just a gut feeling statement.

I do know about the shortcuts to open a terminal to achieve a ordered shutdown but if the crash happens nothing works anymore. The system isn't responding to any keystrokes, all you can do is move the mouse on the screen but that's it!

---

### Post by Impavidus on 2014-01-26
As for an ordered shutdown, try using [alt+SysRq+REISUB](http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses). On some laptops you have to combine it with fn.

---

