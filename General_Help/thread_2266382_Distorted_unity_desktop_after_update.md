---
title: "Distorted unity desktop after update"
date: 2015-02-22
forum: General Help
---

### Post by blue_fox on 2015-02-22
UPDATE 14/05

The unity desktop works again!
Thanks to all who helped to fix the problem!

Arne

---------------------

Hi all,

I'm using ubuntu for a few months now and I'm quite happy with it. But  since last friday evening I'm having trouble with the graphics.
Probably someone else has already encountered the same problem - but I didn't find a related thread on the forums.

Description of the problem:
1. I boot up the PC
2. I login to ubuntu desktop
3. The unity desk loads but it is not only extremely slow (completely  unusable) but the top bar (?) is heavily distorted, the icons on the  left are blank at first but load after 30 seconds or so, the wallpaper  is black and all the 'launch tiles' at the left are covered with  1-pixel big spots of green, red and blue, a few pixels from each  other.

- I found that using the LXDE desktop does not give any problems but the Ubuntu and KDE desktop do.
- The problem is only visible when the nvidia proprietary driver is used  - and only that driver works properly with OpenGL for Google Earth,  OpenCPN, ...
- I did a fresh install and updated it: same problems

Hardware:
HP Pavilion DV5000
Intel centrino T2400 Dual Core
Nvidia Geforce Go 7400

Screenshot of the available drivers:
[IMG]https://lh4.googleusercontent.com/-6YHhKWMDVe4/VOoJy1PyygI/AAAAAAAAAlc/AVShTIQjMhY/w390-h242-no/Screenshot%2Bfrom%2B2015-02-22%2B17%3A51%3A39.png[/IMG]

Has someone an idea how to solve this problem?

Any help will be appreciated.

Update:
 - when booting (only with an external monitor attached?), after the login to LXDE I get a black screen on the auxiliary monitor with a rather small window saying something like 'The system is running in low graphics mode' and then I can choose four options or so. I've acces to a fault report but I can't make much out of it but is seems to be related to Xorg. When I choose to return to the login screen, there's a black screen, I'm unable to enter any text and the traditional login screen doesn't show up.
 - when booting again, the window 'ubuntu internal error' appeared saying it has to do with the unity-greeter.
 - last time, the pointer of my mouse suddenly disappeared while using LXDE.

Hope this helps.

Update:
probably this recent thread is related:
[http://ubuntuforums.org/showthread.php?t=2265631](http://ubuntuforums.org/showthread.php?t=2265631)

Kind regards,

Arne

---

### Post by blue_fox on 2015-02-24
Important, but I forgot to add: I'm using ubuntu 14.04.1 LTS.

Update: sound fixed.

Regards,

Arne

---

### Post by blue_fox on 2015-02-27
Bump!

Is anyone else having similar problems? Would be good to hear I'm not the only one who's having problem with his rather-old (2007) hardware.
I suspect that the issue is due to the updates of thursday the 19th, would it be possible to return certain programs to that state?
I don't now yet which program it is, but it should be related to the unity-desktop environment.

Regards,
Arne

---

### Post by mörgæs on 2015-02-28
This is old hardware and you experience that LXDE is working better than Unity. The problem has persisted for more than a week.

In stead of trying to roll back parts of the updates have you considered a clean install of Lubuntu 14.04.2?

---

### Post by blue_fox on 2015-03-01
Hi,
I'll give it a try.
regards,
Arne

---

### Post by blue_fox on 2015-03-06
[QUOTE=mörgæs]This is old hardware and you experience that LXDE is working better than Unity.[/QUOTE]

I know this... but the Unity desktop worked before the update, even at a very useable speed. But I understand Ubuntu has to move on.
A few days ago the desktop didn't show anything at all, but I just tested it again and now the launch icons remain white squares. The pixel distortion wasn't there anymore, but maybe it only shows up after a few minutes.

I did a system test and it said:
[TABLE]
[TR]
[TD="class: label"]graphics/compiz_check[/TD]
[TD="bgcolor: #f00"]FAILED[/TD]
[TD]Not blacklisted:          no Compiz supported:         no[/TD]
[/TR]
[/TABLE]
I noted that during that system test (in LXDE ...), the status bar at once showed a similar distortion pattern as seen in the desktop before:

[IMG]https://lh5.googleusercontent.com/-YvUBPp0yjoc/VPmU6Ul-BrI/AAAAAAAAAng/P5Z22JtzcII/w640-h480-no/Screenshot%2Bfrom%2B2015-03-06%2B12%3A13%3A43%2Bcrop.png[/IMG]

Best,
Arne

---

### Post by blue_fox on 2015-06-26
Hi,

Some time ago I updated to 14.10 and the issue was gone. Great!
However last week I installed the new version of Kdenlive (my favorite video editor) but it didn't work, I can't save files, video playback was impossible, ...

So I thought: let's upgrade to 15.04. But now it seems this wasn't a good decision - as the Unity desktop doesn't work anymore. Same symptoms as with 14.04.
Kdenlive sort of works but I have to run it as root and not all the icons are displayed in this mode. The good things are that the kdenlive video playback seems to be improved and that the PC boots faster.
The Mate and LXDE desktops work but I really prefer the Unity desktop.

I can do a new install with a 14.10 image and reinstall all my programs - not a very big deal but still some work - but can't this problem be solved in another (more future proof) manner?

Best Regards,

Arne

---

### Post by mörgæs on 2015-06-27
How does 15.04 work in a live boot?

---

