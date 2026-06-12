---
title: "Problems when using touchscreen"
date: 2022-07-17
forum: General Help
---

### Post by pzm9012 on 2022-07-17
Hi there,
 I’m using the live system of Ubuntu 22.04 (“Try Ubuntu”)on Wayland on a computer with touchscreen. However, some problems occur when I’m operating: 
[LIST]
[*]I couldn’t click the “show all applications” button at the lower left corner. Nothing reacts. I have to move my finger from it to somewhere else to open the launcher.
[*]When I long press a file in the file manager, I can see the right-click menu, but it disappears immediately when I release my hand.
[*]When I try to move a window of an application, it can be only moved a bit.
[/LIST]
Are these problems common, or do they just occur on my computer? If there is a solution, could you please tell me how to do that?

---

### Post by ajgreeny on 2022-07-17
Do you have thr same problem if you boot to an X11 session?

---

### Post by pzm9012 on 2022-07-18
Actually&#65292; I can&#8217;t switch to X11 in the live system. The login screen is skipped for there is no password. But I have tried Ubuntu 20.04, which uses X11 as the default session. The first and third problems don&#8217;t occur on 20.04, but some other problems occur, like candidates are not displayed on the screen keyboard. 
I may install Ubuntu 22.04 on the local disk and tried again, but it is a public computer, and I need permission. So I hope these problems can be solved directly.

---

### Post by ajgreeny on 2022-07-18
I have no way to check this personally on a touch screen but you can certainly logout from the wayland session and then login again at the login screen using username ***ubuntu*** and leaving the password blank, just hit enter.

This has always been possible in live systems of Ubuntu so I assume that is still so in a touchscreen version.

---

### Post by pzm9012 on 2022-07-23
There&#8217;s something different when I&#8217;m using touchscreen: after I logout and select the user on the screen, normally it will ask for password, and I can change desktop environment. But actually it enters the desktop directly without asking to input password, so I don&#8217;t have the chance to choose X11. This doesn&#8217;t happen when I use Kubuntu 22.04(on X11). 
I haven&#8217;t tried to change the password of Ubuntu and then log out again. Now I&#8217;m just using Kubuntu 22.04 with Persistence, so that I can install Onboard, and it is faster.

---

