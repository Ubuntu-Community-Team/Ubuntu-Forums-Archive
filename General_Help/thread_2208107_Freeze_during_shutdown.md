---
title: "Freeze during shutdown"
date: 2014-02-26
forum: General Help
---

### Post by ThomasBk on 2014-02-26
Hello,

I'm taking my first steps with Linux.
I have installed Lubuntu 13.10 on an old laptop PC (HP Omnibook VT6200, Pentium 4-M 1.40Ghz, 512 MB RAM, 40GB HDD).
Everything seems to work fine (I had just to correct a problem with Lubuntu Software Center), except an issue with shutdown...
When I select "shutdown" (in italian language), the screen goes black with some text, then it clears and gets dark-green (sometimes a little brighter) with the Lubuntu logo in the middle. This logo has wrong colours, and is animated (blinking dots). After some seconds, the dot animation stops, and nothing happens. I have to turn off the computer "brutally" with the power button.
(The Lubunto logo has wrong colours also during boot, except for a second before disappearing, when it gets coloured correctly -- white and blue if I remember well.)

Do you have any suggestions to solve this?
Thanks

---

### Post by bc.haynes on 2014-02-26
What kind of video does it have? Enter in Terminal:
```
lspci | grep VGA
```
What do you get?

---

### Post by ThomasBk on 2014-02-27
I get the following:

01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV100/M6 [Rage/Radeon Mobility Series]

I also noticed that during boot I get some errors regarding "ali 1535 smbus" (but the boot proceeds anyway).

---

### Post by mörgæs on 2014-02-27
Does it help pressing Enter when the computer seems to sleep during shutdown?

---

### Post by ThomasBk on 2014-02-27
No, it doesn't help.

---

