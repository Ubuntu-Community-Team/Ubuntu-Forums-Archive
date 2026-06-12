---
title: "White  curtain in the middle of the screen... harware problem  or not?"
date: 2014-08-07
forum: General Help
---

### Post by bjngchn on 2014-08-07
Here is what happened: This computer is noisy and gets hot quickly. It is noisy probably because of ventilation. ... Anyway I killed 2 processes just to see whther it helps. Nothing happened but after a while screen was divided in 3 equal vertical stips. Left and right strips are normal. Middle one is problematic. I can hardly see what stays in that region. It is very white. It looks excatly  like a white paper is placed over that region . ........ This is kununtu 13. Maybe I should upgrade to Kubuntu 14, which is easier to install. .... But first I need to know whether there this is a hardware problem which can't be fixed with formatting with a new CD. ... If it is a hardware problem , is it worth fixing? This is a new computer about half year old, but it is problematic already because of noise. White curtain is a serious problem which can make a regular user blind eventually.  .................. There are no other problems besides the  white curtain and old problem noise+heat.................. I feel problem was created by laptops's own heat damaging its own hardware. If so maybe I'm lucky because this happened without fire(?)

---

### Post by Mark Phelps on 2014-08-07
This is almost certainly a hardware problem -- either the laptop video chip and/or the laptop display screen.

if the laptop is running hot, it's possible the video chip could have been damaged by the heat -- but the display dould also be going out.

You could exclude the latter by plugging in an external display and seeing if you still get the "white curtain".  

If so, the video chipset is damaged and is unlikely to be repairable.

If not, the laptop display is going out and would need a complete replacement.

---

### Post by bjngchn on 2014-08-07
Thanks. So this means probably something burnt or melted  inside computer and can't be fixed, or won't be worth fixing.  And computer needs to be put aside or thrown away.  Let's say battery is in and computer is not in use. Can it cause fire by itself?  What can be done to make sure a computer doesn't get too hot ? For example some unnecessary programs can  be stopped, some proccesses can be killed, or some hardware can be removed?   ................ It is very difficult to find a laptop meeting my criteria: big screen, doesn't get hot or noisy, battery is removable, wireless can be disabled mechanically, ... Some bad things become fashion and prevent us from  shopping freely. ... So if you really like something, buy 2 of the same thing.

---

### Post by Mark Phelps on 2014-08-07
>  What can be done to make sure a computer doesn't get too hot ? From your other comments, it seems you're asking this about a laptop, and if that is true, you can get one of those laptop bases that include fans.  They draw heat away from the base of the laptop and cool it down a bit.  

You can also You can try out tlp:

> sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

> sudo tlp start


---

### Post by Impavidus on 2014-08-08
> **bjngchn said:**
> Thanks. So this means probably something burnt or melted  inside computer and can't be fixed, or won't be worth fixing.  And computer needs to be put aside or thrown away.You wrote the computer was 6 months old. It may still be under warranty. This may be bad production, with improperly applied [thermal paste]("http://en.wikipedia.org/wiki/Thermal_paste").> Let's say battery is in and computer is not in use. Can it cause fire by itself?Not that easily, or they wouldn't be allowed to be sold. Of course, *if* a Li-ion battery catches fire the results are quite devastating.> What can be done to make sure a computer doesn't get too hot ? For example some unnecessary programs can  be stopped, some proccesses can be killed, or some hardware can be removed?Make sure the fan can freely rotate and is not damaged, remove dust clogging up vents. Ensure all heat sinks et cetera are properly connected, with properly applied thermal paste. Unless you're working in a very hot environment or you modified the computer so that is produces more heat than it was designed to handle, that should be enough. Getting the best graphics drivers may reduce the heat from the graphics card, but only as long as you don't use it very hard.

---

### Post by tgalati4 on 2014-08-08
What is the make and model of the laptop?  Some are built better than others.

---

