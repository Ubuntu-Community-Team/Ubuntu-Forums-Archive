---
title: "Madcatz Cyborg R.A.T. 7 focus issues"
date: 2013-06-09
forum: General Help
---

### Post by m_sharp on 2013-06-09
Hi,

I am having some issues with a Rat 7 mouse. I am using Ubuntu 13.04 64bit. I have read the following post and tried the suggested fixes in there but am still running into issues.

[http://ubuntuforums.org/showthread.php?t=1528982](http://ubuntuforums.org/showthread.php?t=1528982)

My problem is the same as was listed there with the mouse working for a little bit but when going into applications such as Firefox there will be no ability to click on options.

My problem has been made worse by when I tried the mentioned fixes I was able to generate a xorg.conf file but this has resulted in Ubuntu loading properly except that the unity Window manager will not open and I am having further issues where the resolution is not quite right. Removing the generated xorg.conf file resolves these issues but then I will be back to square one with not being able to use the mouse properly.

I was wondering if it is possible to add the extra lines into the xorg.conf.d system avoiding the resolution problem and allowing me to use the propriety AMD graphics drivers. This would hopefully keep the fix for the mouse.

The code given to add to the xorg.conf is:
```

Section "InputClass"
        Identifier "Mouse Remap"
        MatchProduct "Saitek Cyborg R.A.T.5 Mouse"
        MatchDevicePath "/dev/input/event*"
        Option "ButtonMapping" "1 2 3 4 5 6 7 2 9 10 11 12 0 0 0"
EndSection

```


***edit***
I fixed it. Turns out it was me totally misundersatnding how Xorg works.

To fix it I deleted my generated xorg.conf file and then created a new one with the lines above which worked a treat. 
So if you are having this problem dont worry if you dont have an xorg.conf file just create a new file and add in the lines above to fix it.

---

### Post by pjpweaver on 2014-05-19
I'm having the same problem but only when I plug my mouse in via USB hub.  It's a 5+ year old wireless mouse with no special buttons. Having the problem once I upgraded from 13.10 to 14.04, go to this thread from: [http://askubuntu.com/questions/451080/ubuntu-14-04-mouse-and-window-focus-issues](http://askubuntu.com/questions/451080/ubuntu-14-04-mouse-and-window-focus-issues)

---

