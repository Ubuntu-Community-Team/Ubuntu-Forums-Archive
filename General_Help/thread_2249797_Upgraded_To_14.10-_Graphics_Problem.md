---
title: "Upgraded To 14.10- Graphics Problem"
date: 2014-10-24
forum: General Help
---

### Post by sasafrass452 on 2014-10-24
I've just upgraded Ubuntu to 14.10, & it seems that I have a graphics problem that is now much worse than it was with 14.04. When I move my mouse around the screen, it tends to leave a trail of arrows behind it. Is there anything I can do? Thanks!

---

### Post by findingthebalance on 2014-10-24
I upgraded to 14.10 from 14.04 and had a similar problem, mouse cursor  was jumpy and jittery could not find a solution so reinstalled 14.04 and  all is fine again. I had many problems after upgrading. Just thought  I'd let you know.

---

### Post by sasafrass452 on 2014-10-24
Thanx for the suggestion, though I'd rather not have to install it fresh if I can avoid it. If there's a simpler solution, I'm all ears!

> **findingthebalance said:**
> I upgraded to 14.10 from 14.04 and had a similar problem, mouse cursor  was jumpy and jittery could not find a solution so reinstalled 14.04 and  all is fine again. I had many problems after upgrading. Just thought  I'd let you know.

Well, after trying the 14.10 live CD, I can see that I'd be no better off than I am now. If there's anything I can do to fix this issue, please let me know!

---

### Post by ajgreeny on 2014-10-27
I have come to this thread from your other linked one about a live CD login problem, but to give you any more help we really need to know much more about hardware that you have, specifically the graphic card.

---

### Post by sasafrass452 on 2014-11-04
Well, I found a driver in the software center, & am VERY happy to report that my issues are resolved!!! I was afraid to try it, not knowing what the result would be, but I'm pleasantly surprised.... no.... ECSTATIC.... that I no longer see a trail of blinking arrows, a box/square around the mouse when I hover over pull-down menus, or a flickering mouse on any webpage containing flash content. The problems actually started about a yr ago, though at that time, it was just the flickering mouse. I ignored it, since it was a relatively minor issue, but it got worse with 14.04 & even more worse with 14.10. It made the system nearly impossible to use. But thankfully, these issues are now a thing of the past :) Thankyou to those who were trying to help me!

---

### Post by QIII on 2014-11-04
Hello!

It would be very helpful to other members of the community if you would provide the details of your hardware and just what driver you installed.

As it is, someone with the same problem will have no idea what lessons you learned if they encounter the same problem.  Please allow the entire community to benefit from what you have learned.  That is a large part of why these Forums exist.

Thanks.

---

### Post by sasafrass452 on 2014-11-04
I have an old lenovo laptop, so the video component is on-board & I don't know what kind it is. That's why I was afraid to try the driver, though it was the only one available. I installed the ATI Binary X.Org hardware excelleration driver.

> **QIII said:**
> Hello!

It would be very helpful to other members of the community if you would provide the details of your hardware and just what driver you installed.

As it is, someone with the same problem will have no idea what lessons you learned if they encounter the same problem.  Please allow the entire community to benefit from what you have learned.  That is a large part of why these Forums exist.

Thanks.

Well, unfortunately, I celebrated too soon. The problems have returned. I turned on my laptop just now, & immediately saw the change. I don't know why this is happening. If anyone can help, I'd greatly appreciate it!

Can anyone help?

---

### Post by Mark Phelps on 2014-11-05
>     Can anyone help? 

NOT -- without you providing the video hardware information we've asked for -- more than once!

To find out the make and model video chipset on your PC, open a terminal, enter "lspci" (without the quotes), and look for the line containing "VGA". Post that information back here.

---

### Post by sasafrass452 on 2014-11-06
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

[AMD/ATI] RV620/M82 [Mobility Radeon HD 3450/3470]

> **Mark Phelps said:**
> NOT -- without you providing the video hardware information we've asked for -- more than once!

To find out the make and model video chipset on your PC, open a terminal, enter "lspci" (without the quotes), and look for the line containing "VGA". Post that information back here.

---

### Post by Mark Phelps on 2014-11-07
If you already had the AMD video chipset and did not add that by installing a video card yourself, then you have what is known as Hybrid Graphics -- and there are no simple solutions to that in Linux as the specialized drivers needed are written for Windows.

In addition, AMD dropped their restricted drivers for their HD2x/3x/4x-series cards last summer, and no Ubuntu version newer than 12.04.1 is going to work with the older "legacy" fglrx drivers due to upgrades to the X-server that render those drivers incompatible now.

The link contains information and suggestions for dealing with Intel/AMD Hybrid Graphics: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355]("http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355")

---

### Post by sasafrass452 on 2014-11-08
Well, those suggestions are a bit too much for me to handle. I was hoping for a simple solution, but I guess that's not possible. Looks like another laptop is in my future.... *sigh*

> **Mark Phelps said:**
> If you already had the AMD video chipset and did not add that by installing a video card yourself, then you have what is known as Hybrid Graphics -- and there are no simple solutions to that in Linux as the specialized drivers needed are written for Windows.

In addition, AMD dropped their restricted drivers for their HD2x/3x/4x-series cards last summer, and no Ubuntu version newer than 12.04.1 is going to work with the older "legacy" fglrx drivers due to upgrades to the X-server that render those drivers incompatible now.

The link contains information and suggestions for dealing with Intel/AMD Hybrid Graphics: [http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355](http://askubuntu.com/questions/205112/how-do-i-get-amd-intel-hybrid-graphics-drivers-to-work/288355#288355)

---

### Post by joselotl on 2014-11-29
Maybe it's a little too late for a response, but I had a similar problem. What happened was that ubuntu believed that I had a second monitor connected (wich I don't). Just head over to Activities > Displays and disable the second monitor if you have one.

---

### Post by hari6 on 2014-11-29
> **sasafrass452 said:**
> Can anyone help?

I had exactly the same problem. Go to System Settings > Display. Select Unknown Display (or an extra Built-In Display) and turn it off, then click Apply. In my case I had identical displays of green and pink color. I disabled the green one and it solved it. By chance if you selected the wrong option and turned it off, your screen may go black, but don't worry, within 30 seconds it will revert back. Then you can select the other option and your problem will be solved.

---

