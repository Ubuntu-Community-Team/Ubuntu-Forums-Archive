---
title: "ATI RADEON 9600 pro problems"
date: 2008-05-01
forum: General Help
---

### Post by ricky_cullen on 2008-05-01
ok i need help! stuck on 800*600 after tryin to install Drivers from following:
[http://ubuntuforums.org/archive/index.php/t-285125.html](http://ubuntuforums.org/archive/index.php/t-285125.html)

it was working fine till i meteled with it. I even had Compiz fusion workin before i even had the drivers.
I have a ATI Radion 9600 pro i have also tried the restriced drivers and they refuse to stay enabled](*,). im startin to wounder if my card is really even supported because of the trouble i've had with it not wanting to stay enabled i have tried everything i can think on and need help!

---

### Post by jocko on 2008-05-01
That link does not describe any driver installation, it just tells you how to manually configure **nvidia** drivers to fix some **old** resolution issue.
As you said, you have an ati card, so those instructions will never help you (but they will mess things up).
Or maybe you pasted the wrong link?

To get things working properly, try this:

First make sure you have a clean xorg.conf:
```
sudo dpkg-reconfigure xserver-xorg
```Then use the restricted-manager (System --> Administration --> Hardware Drivers (or whatever its name is, I just translated from swedish)) to install and enable the drivers.

Reboot. Now it should work. I have a Radeon 9600 Pro, which works just fine that way.

---

### Post by ricky_cullen on 2008-05-01
ok this works, thanks very very much :) however it shot my refresh rate up for my monitor couldn't handle how do ya fix that? do i need to edit Xorg?

---

### Post by jocko on 2008-05-02
> **ricky_cullen said:**
> ok this works, thanks very very much :) however it shot my refresh rate up for my monitor couldn't handle how do ya fix that? do i need to edit Xorg?

If you know which refresh rates your monitor can handle, you can add the refresh rate ranges to xorg.conf. You can probably find these in your monitor manual (which you may find on the manufacturers home page).

```
sudo gedit /etc/X11/xorg.conf
```Find 'Section "Monitor"' and add your ranges like this:
```
HorizSync       [COLOR=Gray]30-110[/COLOR]
VertRefresh     [COLOR=Gray]50-150[/COLOR]
```

---

### Post by ricky_cullen on 2008-05-02
Thank you very much that worked perfectly :biggrin:

---

