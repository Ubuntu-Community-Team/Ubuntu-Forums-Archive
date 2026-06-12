---
title: "Problem with dual monitor resolution"
date: 2014-07-22
forum: General Help
---

### Post by damian11 on 2014-07-22
This is my first post so i'd like to say hello.

I have problem with resolution in my monitors - in more details i have 2 monitors attached to my pc, both have resolution 1440x900, but I can only set 1024x768.
When i have only one monitor i can set normal resolution which is 1440x900 (LG W1952TQ) but when i attach only second monitor (LG W1942S) in settings i have unidentified monitor and only 1024x768. 
I also have windows and on windows i solve issue by install PowerStrip. I already read about X/Config/Resolution and try to something set but with no success.

If anyone could help me with my issue it will be great.

Best regards.

---

### Post by QIII on 2014-07-22
Hello!

It would be very helpful if you would tell us the hardware specifications of your machine and whether you have any proprietary drivers installed.

---

### Post by damian11 on 2014-07-22
My hardware specifications:

Graphic: RADEON X600/X550 Series (Microsoft Corporation - WDDM) (128 MB)
I have installed ATI Catalyst&#8482; 9.3 Proprietary Linux x86 Display Driver 

If some more specifications will be helpful, please let me know.

---

### Post by Bucky Ball on 2014-07-22
Welcome. Have you got Catalyst Control Centre installed? That might bring some joy.

I've had success using arandr getting resolutions I otherwise couldn't. You can install it from Software Centre and it should end up in Accessories. (Using xfce4 so not sure on Unity.)

---

### Post by QIII on 2014-07-22
Graphics adapters that old and a driver that old? What version of Ubuntu are you using?

---

### Post by Bucky Ball on 2014-07-22
> **QIII said:**
> Graphics adapters that old and a driver that old? What version of Ubuntu are you using?

^^^
This. Just noticed. ;)

---

### Post by Mark Phelps on 2014-07-22
Since ATI catalyst v9.3 came out in 2009, my guess is they're running Ubuntu 9.04 or 9.10.  Either way, that's way past EOL.

---

### Post by damian11 on 2014-07-24
@ Bucky Ball
I have installed ATI Catalyst&#8482; 9.3
I also try arandr but after installation i have some error and program not start.

I have Ubuntu 12.04.4 LTS

---

### Post by QIII on 2014-07-24
Hello!

That adapter is no longer supported by AMD/ATI with any proprietary driver at all.  Even HD 2000 to HD 4000 series are not supported beyond 12.04.1

You will need to remove whatever you have installed and stick with the default open source Radeon driver installed with *buntu.

---

### Post by damian11 on 2014-07-24
I unistall drivers from AMD but still there is no effect. I install drivers from AMD because i have issue with resolution even on fresh installation. I can set proper resolution when I have only LG W1952TQ attached. When i have attached only LG W1942S i have unknown in settings and only resolutions: 1024x768 and 800x600.

---

### Post by damian11 on 2014-07-25
I forget to write that i have attached monitors by digital and analog cabel, but when i switch cabels there is still the same problem with W1942s. It's a weird because at work i have attached 2 samsung monitors and I have no problem, everything works fine with no addition drivers. Maybe my monitor is no supported by ubuntu ? There is any solutions to solve that ? I read about [COLOR=#333333]xrandr but probably i set something incorrect.
[/COLOR]

---

