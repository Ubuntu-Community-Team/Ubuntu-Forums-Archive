---
title: "Multiple Monitor functionality question"
date: 2008-04-09
forum: General Help
---

### Post by CarollaTony on 2008-04-09
I have set up Gutsy Gibbon, and enabled two monitors \\:D/ .  My hardware is as follows:

NVidia 8800 GTX (Thanks to Envy for driver setup)
Samsung SyncMaster226BW DVI connected (left side of desk)
ViewSonic VA930M DVI connected (right side of desk)

What I am trying to do is start a firefox window on each screen.  I get an error when I try to start a session on the other screen, because it says that Firefox is already running (duh) :confused: .  And if I start a new window on the same monitor, I can't drag it to the other monitor.  ](*,)

Is there a way to do this?  

Also, I noticed that when I start a program on the second monitor, there is no title bar to drag the window, or size it.  FF lets me go full-screen, but I can't resize of move them.  

TIA

---

### Post by redbob on 2008-04-09
Have you activated twin-view option in xorg.conf or both monitors shows the same image?

---

### Post by bodhi.zazen on 2008-04-09
There are two issues.

first firefox, try starting the second session with :

```
/usr/bin/firefox -p -no-remote
```

second, it sounds as if nvidia is not quite configured properly.

Try ```
gksu nvidia-settings
```

Enable twinview as opposed to separate monitors. You will need to save the changes and re-start X (log out and back in).

HTH

---

### Post by RedPandaFox on 2008-04-09
I get the same problem (duel heads with 6600GT)
Nvidia all configured correctly, Im assuming it is because it conciders both moniters diffrent views both trying to access the same information?

---

### Post by CarollaTony on 2008-04-10
:cool: Thanks Bodhi! :cool:

Twinview was exactly what I needed.  Also, I noticed that the mouse actions (menus, right-clicks) were very slow on my main (left) monitor.  But now they are screaming on both monitors.  

This little exercise also shows me how much I have to learn about X though.  

RedPandaFox:  try ```
gksu nvidia-settings
``` and setting twinview on.  From the settings window, in the upper left choose 'X Server Display Configuration'.  Then on the right, towards the bottom click 'configure'.  In the requester, choose TwinView (requires X restart).  Then click Apply, do a restart, and you should be good to go.

---

### Post by redbob on 2008-04-23
Wellwellwell... livin'n'learnin.. 'livin'n'kickin'... nvidia-settings is great!! 
:lolflag:

---

