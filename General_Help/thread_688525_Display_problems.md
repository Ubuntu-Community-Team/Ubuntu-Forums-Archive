---
title: "Display problems"
date: 2008-02-05
forum: General Help
---

### Post by lukataylo on 2008-02-05
hi guys i have just installed Ubuntu and i encountered some display problems for my screen as there are no drivers for it released it comes up with distortion (lines ) i tried configuring size refresh rate etc but still does that here is the detailed specification

**19" HannSpree AH191 Widescreen/DVI TFT **

SPECIFICATIONS
                    Driving system TFT Color LCD
LCD Panel           Size           48.2cm(19.0")
                    Pixel pitch    0.285mm(H) x 0.285mm(V)
                                   R,G,B Analog Interface
                    Video
                                   Digital (Dual-Input Model) H/V TTL
Input               H-Frequency    31KHz &#8211; 80KHz
                    V-Frequency    55 &#8211; 75Hz
Display Colors                     16.2M Colors
Max. Resolution                    1440 x 900 @75Hz
                                   VESA DDC2BTM
Plug & Play
                    ON Mode        &#8804;36.7W
EPA ENERGY STAR®
                    OFF Mode       &#8804;2W
                                   Rated Power 1.5W rms (Per channel)
Audio output
                                   D-Sub 15pin
Input Connector
                                   DVI-D 24pin (Dual-Input Model)
                                   Hor. :376.2mm
Maximum Screen Size
                                   Ver. :301.06mm
Power Source                       100~240VAC,50/60HZ
                                   Operating Temp: 5° to 40°C
Environmental
                                   Storage Temp.: -20° to 60°C
Considerations
                                   Operating Humidity: 20% to 80%
                                   440(W) x 358(H) x 207(D) mm
Dimensions
                                   17.33(W)×14.11&#8221;(H)×8.16&#8221;(D)
                                   5.5 kg / 4.5 kg
Weight (GW/NW)
                                   12.1 lb / 9.9 lb

MMore infor; First of all i also have windows p and it runs perfectly on that and My graphics card is: Sylicon integrated systems sis chipset

please help:confused:

---

### Post by phidia on 2008-02-05
I don't know if the problem is with your screen...what gpu (video card) is your system using?
You will need to select, or enable the correct driver for your gpu as well as trying to get the right display parameters.
Once you know what video card you have you can check out the[ multimedia & video forum]("http://ubuntuforums.org/forumdisplay.php?f=138").

---

### Post by lukataylo on 2008-02-05
i have a sis integrated video card and i also have xp and it runs perfectly with xp

---

### Post by phidia on 2008-02-06
You can use the script/program in debian based systems to set up your video card.
Open a terminal and copy and paste this: > sudo dpkg-reconfigure -phigh xserver-xorg select the sis driver and the resolution your monitor uses and restart x (Alt+Ctrl+backspace)
See the links belows for more details.

Refrences: [No openGL Accel]("http://ubuntuforums.org/showthread.php?t=680296&highlight=sis+graphics+card")  [Rez problems]("http://ubuntuforums.org/showthread.php?t=689114&highlight=phigh")

---

### Post by lukataylo on 2008-02-06
i should admit this has improved the monitor display but the pronlem is still there when you run applications etc and also i didn't quite understand what you do after you eneter the code into terminal and reboot

---

### Post by phidia on 2008-02-06
> **lukataylo said:**
> i should admit this has improved the monitor display but the pronlem is still there when you run applications etc and also i didn't quite understand what you do after you eneter the code into terminal and reboot

What specifically are you seeing? Try to describe it to the thread in ways that will help us help you-that is with detail and actual reproducible symptoms.

I did include those reference links for more detail in my previous post. If you chose the sis driver and the correct resolution for your monitor that should have it working.

You can post your /etc/X11xorg.conf file & your monitor specs here or at the [multimedia & video forum]("http://ubuntuforums.org/forumdisplay.php?f=138").

---

