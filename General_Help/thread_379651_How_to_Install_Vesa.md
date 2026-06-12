---
title: "How to Install Vesa"
date: 2007-03-08
forum: General Help
---

### Post by Eminem on 2007-03-08
How do I install the Vesa Driver? I figured, that's what I need for my X Server problem.

---

### Post by bernied on 2007-03-08
> **Eminem said:**
> How do I install the Vesa Driver? I figured, that's what I need for my X Server problem.
```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the bit on video cards, select the vesa one. It might be just called VGA, or something else very generic.

---

### Post by Eminem on 2007-03-08
> **bernied said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
When you get to the bit on video cards, select the vesa one. It might be just called VGA, or something else very generic.
I can't even boot into Ubuntu. I need to install it in Windows.

---

### Post by bernied on 2007-03-08
Can you get a text login in recovery mode? If you can't, then this will almost certainly not fix your problem. 
But, this is how you can do it the hard way...

Can you access files on your ubuntu install through windows? if not, you will need a live-cd (the ubuntu install cd would do).

The file you need to edit is /etc/X11/xorg.conf

Add a section like this:
```
Section "Device"
        Identifier      "Generic VGA"
        Driver          "vesa"
EndSection
```put it somewhere near another one that looks similar.

Then you need to specify using that device. Look for this bit:
```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV280 [Radeon 9200 PRO]"
        Monitor         "CMC 17 AD"
```Don't expect your entries to be the same as mine. You probably have a different graphics driver installed. 
In this bit, you need to change the 'Device' line so that it specifies the device you defined earlier:
```
Device "Generic VGA"
```

---

### Post by Eminem on 2007-03-08
Since my Graphics Card is an ATI Radeon 7000, this would be my line?:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. [Radeon 7000]"
EndSection
```

Or:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic VGA"
EndSection
```

---

### Post by Eminem on 2007-03-08
> **bernied said:**
> Can you get a text login in recovery mode?

Wait, yes. Yes, I can.

What do I do now?

---

### Post by bernied on 2007-03-08
> **Eminem said:**
> Wait, yes. Yes, I can.

What do I do now?
Login, then do what I said in my first post:
```
sudo dpkg-reconfigure xserver-xorg
```You may need your password once more.
Read everything carefully and accept the defaults for anything that you are not sure about, except for the video card driver, choose the vesa driver.

---

### Post by Eminem on 2007-03-10
How do I perform a "text login"?

---

### Post by taurus on 2007-03-10
When you boot into recovery mode, you already log in as root so no need to log in anymore.  At the prompt, run

```
dpkg-reconfigure xserver-xorg
```
Make sure you pick **vesa** as a driver for your graphic card.  When done, reboot with

```
shutdown -r now
```

---

