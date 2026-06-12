---
title: "Functionality in extra mouse buttons"
date: 2008-03-27
forum: General Help
---

### Post by Colro on 2008-03-27
I've got a Logitech MX518:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16826104178](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104178)

There's four extra buttons on this mouse that I'd like to get working properly if it's at all possible. First of all, the side buttons are automatically assigned to forward/backwards in browsers and such in Windows. I'd love to see that possible again as I've grown quite used to it on my other machines. Also, on the top of the mouse there's two buttons to swap between 1800 DPI and 800 DPI. Those two aren't as important to me, but it'd be nice if I could gain their functionality as well. Any help would be appreciated.

---

### Post by schtufbox on 2008-03-27
The buttons on top are, I believe, software independant, they'll work whatever your OS is, I know mine work fine in linux/windows.

As for the two sidebuttons, they'll work just fine too, but for that you need to edit your xorg.conf ( it's in /etc/X11/ )  Before editing xorg.conf , make sure you back it up, just in case :D


here's what mine says:

> Section “InputDevice”
Identifier “Configured Mouse”
Driver “mouse”
Option “CorePointer”
Option “Protocol” “ExplorerPS/2&#8243;
Option “Emulate3Buttons” “true”
[B]Option “Buttons” “7&#8243;
Option “ZAxisMapping” “4 5&#8243;
Option “ButtonMapping” “1 2 3 6 7&#8243;[/B]
EndSection
The section in bold is what you'll need to add to get the full use of your mouse. Once you've edited xorg.conf you'll need to restart X.

---

