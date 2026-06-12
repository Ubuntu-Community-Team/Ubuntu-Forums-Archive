---
title: "No desktop after login"
date: 2014-06-03
forum: General Help
---

### Post by imperiul on 2014-06-03
Today my 14.04 updated itself not requiring a reboot. After a while I rebooted because of other reasons and then I was pleasantly surprised by a blank screen.

I have tried everything I could think about including
[LIST]
[*]Reinstalled compiz, unity, ubuntu-desktop, xorg
[*]Reinstalled and then removed the nvidia driver
[/LIST]

So far nothing has worked. Except for one little thing: my cairo-dock is showing. And that's all.

Does anybody know what else I could try?

---

### Post by imperiul on 2014-06-04
_**UPDATE:**_

```
sudo dpkg-reconfigure xserver-xorg
sudo service lightdm stop
sudo service lightdm start

```

When I run that code and then login again the icons on the desktop are displayed but the menu and the launcher are still not there.
Also, when I try to run an application from CTRL + ALT + F1 such as ```
dconf reset -f /org/compiz/
``` it says ```
Cannot autolaunch D-Bus without X11 $DISPLAY
```
I can only run applications with ```
export DISPLAY=:0
```

---

### Post by imperiul on 2014-06-06
[COLOR=#333333][FONT=UbuntuRegular]I've reinstalled my OS and everything went fine until it updated again. After the update, unity is once again unusable.
[/FONT][/COLOR]

---

### Post by computer3 on 2014-06-06
> **imperiul said:**
> [COLOR=#333333][FONT=UbuntuRegular]I've reinstalled my OS and everything went fine until it updated again. After the update, unity is once again unusable.
[/FONT][/COLOR]

You're not the only one with this problem. It's happened to me and other people. I've tried to fix it but nothing has worked so far. Hopefully this issue will be fixed soon.

---

### Post by ap0ll0uk2 on 2014-06-06
Yep, make that **3** of us!

I'm pretty sure my system had applied updates on Wesnesday, but I shut the box down and went to bed and didn't see the issues until I started the box up yesterday.

Out of curiousity, which GPU do you both have?

---

### Post by imperiul on 2014-06-06
Nvidia GT 540M

EDIT: Also, it seems like WebGL doesn't work anymore.

---

### Post by computer3 on 2014-06-06
Processor: AMD-E40 APU with Radeon HD Graphics x2 
Graphics: Gallium 0.4 on AMD PALM
OS Type: 64bit
Memory: 3.5g     

Yesterday is when the issues started for me as well.

Here is my original post and the post of someone else who is having the same problem. 

[http://ubuntuforums.org/showthread.php?t=2228071](http://ubuntuforums.org/showthread.php?t=2228071) 

[http://ubuntuforums.org/showthread.php?t=2228084](http://ubuntuforums.org/showthread.php?t=2228084)

---

