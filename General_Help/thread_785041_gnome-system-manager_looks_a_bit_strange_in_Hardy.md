---
title: "gnome-system-manager looks a bit strange in Hardy"
date: 2008-05-07
forum: General Help
---

### Post by petteRiK on 2008-05-07
Hi

I have updated my IBM T40 laptop from Gutsy to Hardy. Installing Gutsy to my laptop went without any problems and the updating was successful also. But afterwards I noticed that the system manager looks like the texts are shifted couple centimeters to the left and I have to point with mouse those couple centimeters to right to select for example exit button. All texts and lines are various colours, not black like they should be. The system manager window looks like it is made two blocks: all texts are on the top block and behind it there is a block where all buttons and other selectors are. I have print screen here: [http://koti.mbnet.fi/isukki65/jarjestelmanvalvonta.png](http://koti.mbnet.fi/isukki65/jarjestelmanvalvonta.png) 

I have reinstalled the gnome-system-manager several times and several versions. Always the result is same. Also there are no difference how I start the application. But when I started the system manager from the console it gives a warning that SELinux is installed but not enabled. 

Any other application doesn't act like this. Can you please help me to solve this problem.

---

### Post by kpkeerthi on 2008-05-07
Do you have visual effects turned on? Seems like a video driver issue. Turn off visual effects from System -> Preference -> Appearance -> Visual Effects.

---

### Post by petteRiK on 2008-05-07
> **kpkeerthi said:**
> Do you have visual effects turned on? Seems like a video driver issue. Turn off visual effects from System -> Preference -> Appearance -> Visual Effects.

Visual effects are turned off. Actually I can't even turn them on. I think the reason for visual effect denial is the display adapter or driver(VESA).

---

### Post by petteRiK on 2008-05-09
:D Great, I got it working. The problem was the driver. In my T40 the graphic card is *ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]* and somehow the Hardy mess my system manager if I use VESA driver. I changed the driver to **ati** and broblem has gone. I find out pages [http://lilserenity.wordpress.com/2007/07/31/installing-ubuntu-feisty-fawn-704-on-a-thinkpad-t40/](http://lilserenity.wordpress.com/2007/07/31/installing-ubuntu-feisty-fawn-704-on-a-thinkpad-t40/) and [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver) very helpful. Now I can even use compiz if I want but it takes so much CPU time that I rather work whithout it. So thaks for the whole forum and keep going good work.

---

