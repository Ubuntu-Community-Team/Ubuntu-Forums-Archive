---
title: "Installing Nautilus actually installs Dolphin/Konqueror"
date: 2012-12-31
forum: General Help
---

### Post by Carl H on 2012-12-31
I've found a few issues/limitations with Thunar and have read that Nautilus can be installed on Xubuntu.

So I did ```
sudo apt-get install nautilus
``` and restarted the system when asked. 

On reboot, there was no sign of Nautilus, but I did have Dolphin and Konqueror installed! 

What gives?

---

### Post by sudodus on 2012-12-31
Strange! What version and flavour of Ubuntu are use running?

I have done it more than once in Lubuntu 12.04, and it worked for me (giving me Nautilus). What if you try from a terminal window
```
nautilus --no-desktop
```

---

### Post by Carl H on 2012-12-31
Correction:
I just did a dpkg --list and Nautilus was listed, as are Dolphin and Konqueror.

---

### Post by Carl H on 2012-12-31
> **sudodus said:**
> Strange! What version and flavour of Ubuntu are use running?

I have done it more than once in Lubuntu 12.04, and it worked for me (giving me Nautilus). What if you try from a terminal window
```
nautilus --no-desktop
```

Yes, that does fire up Nautilus, thanks. And it recognises my camera, which Thunar and Dolphin failed to do. 

Is it possible to set Nautilus as the default file manager?

---

### Post by Carl H on 2012-12-31
> **Carl H said:**
> Is it possible to set Nautilus as the default file manager?

Easy enough from the Settings Manager. Sorry, I should have just tried before I asked. :D

---

### Post by sudodus on 2012-12-31
Sometimes it helps to discuss with someone, and you will find out more or less by yourself. Good luck and welcome back :-)

... and please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

### Post by Elfy on 2012-12-31
> **Carl H said:**
> I've found a few issues/limitations with Thunar and have read that Nautilus can be installed on Xubuntu.

So I did ```
sudo apt-get install nautilus
``` and restarted the system when asked. 

On reboot, there was no sign of Nautilus, but I did have Dolphin and Konqueror installed! 

What gives?Are you sure it installed at the same time? If it did then what version of xubuntu - would be a bug. 

I know when I installed nautilus here it didn't.

> **sudodus said:**
> ...
```
nautilus --no-desktop
```Not sure you need the no desktop palaver anymore - works ok here without causing issues.

---

### Post by sudodus on 2012-12-31
> **Elfy said:**
> ...
Not sure you need the no desktop palaver anymore - works ok here without causing issues.

Good news :-)

---

### Post by Carl H on 2013-01-01
> **Elfy said:**
> Are you sure it installed at the same time? If it did then what version of xubuntu - would be a bug. 

It's Xubuntu 12.10 64-bit. Dolphin & Konqueror both appeared after I'd installed Nautilus. I also installed Digikam prior to Nautilus, possibly it was that that brought them in and I didn't notice.

---

### Post by ibjsb4 on 2013-01-01
> **Carl H said:**
> It's Xubuntu 12.10 64-bit. Dolphin & Konqueror both appeared after I'd installed Nautilus. I also installed Digikam prior to Nautilus, possibly it was that that brought them in and I didn't notice.

Digikam installs kde packages.

If you install Synaptic Package Manager, it will tell you what packages are going to be installed before you do the install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by sudodus on 2013-01-01
> **ibjsb4 said:**
> Digikam installs kde packages.

If you install Synaptic Package Manager, it will tell you what packages are going to be installed before you do the install.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=synaptic+package+manager&as_qdr=all&sa=Google+Search&lang=en)
+1
Digikam belongs to KDE, which is tightly integrated.

---

