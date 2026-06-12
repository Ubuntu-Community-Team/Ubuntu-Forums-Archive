---
title: "uguntu gnome desktop right up corner 4 logos"
date: 2017-06-25
forum: General Help
---

### Post by ubunt2017m on 2017-06-25
Hello

I have installed ubuntu gnome and read my instructions available
but could not find explanation to:

right up corner, last of four logos to click, then comes down menu
where in bottom is 4 pictures, : 1 from left= settings, then 2nd is somekind lock on / off .. now what is this for?

because 3rd picture is screen lock and then last is power on/off alternatives.

I just can not yet understand what that 2nd option at left does.. so thank you if you can help how to use it (or not).

---

### Post by RobGoss on 2017-06-25
Did you try clicking on it to see it's function?

---

### Post by vasa1 on 2017-06-25
Isn't a tooltip available when you hover the mouse pointer over the icons?

---

### Post by ubunt2017m on 2017-06-25
> **RobGoss said:**
> Did you try clicking on it to see it's function?

Yes, only activity i see happen, it changes like on or off, but i dont know for what. I can not notice difference?

And for those 4, there comes no tooltips or anything , when mouse hover on or off near them.

But those 3 /4 are like i write, well known. 

I found it weird someone put there instructions in my language, but there is only about screen lock, that is next to it, this one remains mystery.

I could only guess, things like: if on-locked, system may ask more password or off, not ask ?

---

### Post by vasa1 on 2017-06-25
Did you try to right-click on them?

---

### Post by ubunt2017m on 2017-06-25
> **vasa1 said:**
> Did you try to right-click on them?


Yes, right click too not open any more information.

Only thing that happens, is they change from dark color to more light, when mouse is on or off near them.

---

### Post by RobGoss on 2017-06-25
What version of Ubuntu Gnome are you using? I have Ubuntu Gnome 16.04.2 loaded up on a **USB** and running the live desktop but I'm not even seeing these four button options. Do you see these buttons when logging out of something

---

### Post by ubunt2017m on 2017-06-25
Yes well where i could see what this version is, i update that later to text. Ubuntu 16.04.2 LTS 64-bit

But of course that picture can not be anything else than , belongs more to mobile devices, like phones or tablets.

If you move screen, it would lock rotation, so it would keep in one position always.

I guess this installation have some mobile abilities, not needed when should be home computer settings, like desktop or laptop.
Laptop i use. No would not need that lock, or no matter how it is in position , on or off?

I also noticed, i was at other forum day ago, it shows me first mobile view, which is more limited. So that forum thought i was using mobile,
although i was using laptop?
But all other websites and forums i have visit, show computer view, that may have been temporary settings wrong in one website then.
But it seems continue, i try solve if their problem or somehow with my system settings could show mobile is here to somewhere?

---

### Post by vasa1 on 2017-06-25
Please paste the following code into a terminal```
echo -e "Version $(lsb_release -a)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Kernel info: $(uname -a)"
``` then press **enter** and post the output here

---

### Post by howefield on 2017-06-25
> **ubunt2017m said:**
> But of course that picture can not be anything else than , belongs more to mobile devices, like phones or tablets.

If you move screen, it would lock rotation, so it would keep in one position always.

That is what it is, an orientation function. Although not sure why you are seeing it on (presumably) a desktop.

> Screen orientation

    Configurable orientation-based automatic rotation using accelerometer/gyroscope/magnetometer
    Both the shell and apps should be able to switch orientation based on sensors
    Support for orientation input from many sources, including iio, i2c, and usb devices
    Easy ability to temporarily disable and enable auto-rotation (rotation lock)
    Rotation lock or other rotation commands should be easy to bind to hardware buttons
    Some applications might want to lock the screen in a particular direction, for example, landscape for a game (or a video player in some cases)

    673075 improved orientation settings in "Displays" panel for touch devices 

---

### Post by ubunt2017m on 2017-06-25
> **vasa1 said:**
> Please paste the following code into a terminal```
echo -e "Version $(lsb_release -a)
Session: $DESKTOP_SESSION
Desktop: $XDG_CURRENT_DESKTOP
Kernel info: $(uname -a)"
``` then press **enter** and post the output here

No LSB modules are available.
Version Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.2 LTS
Release:	16.04
Codename:	xenial
Session: gnome
Desktop: GNOME
Kernel info: Linux (username just here) 4.8.0-56-generic #61~16.04.1-Ubuntu SMP Wed Jun 14 11:58:22 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux


Yes there is output. Guess i can publish most of that, username part not probably good .. :) .. not contain technical information of system that.

---

### Post by howefield on 2017-06-25
Is the device that you have installed Ubuntu Gnome on some sort of tablet or similar ?

---

### Post by ubunt2017m on 2017-06-25
> **howefield said:**
> Is the device that you have installed Ubuntu Gnome on some sort of tablet or similar ?

No, should not have much connection to mobility. Laptop acer aspire one. 

But i use to internet share mobile device, lumia phone 4g then i put wifi on at laptop where gnome is and write password to wifi connection.

I dont know if that connection could find then some reason to think laptop is mobile too, when internet comes from mobile phone share?

---

