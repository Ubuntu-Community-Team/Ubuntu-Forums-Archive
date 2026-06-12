---
title: "[SOLVED] Changing Screen Resolution Refresh Rate"
date: 2008-06-06
forum: General Help
---

### Post by cybrsaylr on 2008-06-06
I'm running Hardy and wondering if there is any way to change the 'refresh rate' from the default 60 Hz, to 70Hz, 75Hz, or higher to ease eye strain? This was easy to do in Windows but I can't find a way to do it in Ubuntu.

---

### Post by iaculallad on 2008-06-06
Navigate to System->Administration->Screen and Graphics, On the "Screen" tab,  select your screen and change your Refresh rate (Resolution ______ at Refresh rate)then click on OK.

---

### Post by cybrsaylr on 2008-06-06
In my Hardy Heron:

When I Navigate to System->Administration->there is no 'Screen and Graphics' from the dropdown choices?

---

### Post by peakshysteria on 2008-06-06
In terminal:

```
sudo displayconfig-gtk
```


(alt: System --> Prefrences --> Main menu --> Other --> Check screens and graphics and you'll find it under: Applications --> Others)

---

### Post by iaculallad on 2008-06-06
> **cybrsaylr said:**
> In my Hardy Heron:

When I Navigate to System->Administration->there is no 'Screen and Graphics' from the dropdown choices?

What I just post was for Gutsy. Let's try doing it in Hardy manually:

Create a backup of your current xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Open it for editing:

```
sudo gedit /etc/X11/xorg.conf
```

Then paste the line below (bottom part) to the "Monitor" section of your xorg.conf file and save it:

> HorizSync 30-110
VertRefresh 50-160

Output should be like this (Sample only - Different from yours):

```
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 30-110
        VertRefresh 50-160
EndSection

```

---

### Post by Erlander on 2008-06-06
System/Preferences/Screen Resolution is where you find it.

Rob

---

### Post by cybrsaylr on 2008-06-07
> **iaculallad said:**
> What I just post was for Gutsy. Let's try doing it in Hardy manually:

Create a backup of your current xorg.conf file:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Open it for editing:

```
sudo gedit /etc/X11/xorg.conf
```

Then paste the line below (bottom part) to the "Monitor" section of your xorg.conf file and save it:

Then paste the line below (bottom part) to the "Monitor" section of your xorg.conf file and save it:

Quote:HorizSync 30-110
VertRefresh 50-160 

Output should be like this (Sample only - Different from yours):

Code:
Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync 30-110
        VertRefresh 50-160
EndSection

OK, did all that and still can't change 'refresh rate' that is still locked in at 60Hz.
The Screen Resolution is the only thing I can change but the Refresh Rate won't change from 60Hz, the default setting. On Windows you can change it from 60Hz-95Hz to ease eye strain @ 60Hz.

---

### Post by Pjotr123 on 2008-06-07
Have you already installed the right driver for your video card?
[http://ubuntutip.googlepages.com/thefirstthingstodo](http://ubuntutip.googlepages.com/thefirstthingstodo)
(number 2 )

Check that first. Then:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 as well)

Greeting, Pjotr.

---

### Post by cybrsaylr on 2008-06-07
> **Erlander said:**
> System/Preferences/Screen Resolution is where you find it.

Rob
Yeah I found it no problem.
The problem is changing the 60Hz refresh rate to say 70Hz or 75Hz.
The screen resolution changes easily but the refresh rate seems locked at 60Hz.

---

### Post by rlhawk1 on 2008-06-11
I'm having the same problem.  I was running in 1024x768 at 70Hz, then the power went off, and now I can't set it to anything besides 60hz.  Everything still works fine in windoze, so I don't think my card was damaged or anything.

I'm using an ATI Radeon X300 pci express card.  Any ideas?

-----

Okay, I was able to fix this problem by doing this: 'sudo displayconfig-gtk' then setting the screen model to my exact monitor.  After doing that, I was able to change my refresh rate using the System->Preferences->Screen Resolution program.  I think setting the screen model with the displayconfig-gtk program somehow made it regenerate the list of available resolutions/refresh rates.

---

### Post by Xasz on 2008-06-12
Been searching everywhere for a solution to this. My Ubuntu install has to stay on ice until I get this fixed, my eyes start throbbing after only 20 minutes of using it

To make things harder, I'm using dual monitors: 1440x900 (wide screen) and 1280x1024. Both should use 70hz, but I'm having this same issue. Ugh

---

### Post by cybrsaylr on 2008-06-14
> **rlhawk1 said:**
> 
Okay, I was able to fix this problem by doing this: 'sudo displayconfig-gtk' then setting the screen model to my exact monitor.  After doing that, I was able to change my refresh rate using the System->Preferences->Screen Resolution program.  I think setting the screen model with the displayconfig-gtk program somehow made it regenerate the list of available resolutions/refresh rates.
Thanks rlhawk1.
 I did what you suggested and it solved my problem.
Now I can change the refresh rates where before they were locked at 60Hz. What a relief to my eyes.

---

