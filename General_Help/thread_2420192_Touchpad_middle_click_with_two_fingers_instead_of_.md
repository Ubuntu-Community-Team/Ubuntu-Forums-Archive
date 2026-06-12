---
title: "Touchpad middle click with two fingers instead of three?"
date: 2019-05-31
forum: General Help
---

### Post by annanu2 on 2019-05-31
According to this [https://help.ubuntu.com/stable/ubuntu-help/mouse-middleclick.html.en](https://help.ubuntu.com/stable/ubuntu-help/mouse-middleclick.html.en) , three fingers tap is assigned  to middle click. Is there a way to change that to two finers tab. 
The solution I used below for the older version of Ubuntu doesn't seem to work any more with 18.04   

[COLOR=#202124][FONT=Roboto]Add these to .bashrc[/FONT][/COLOR]
[COLOR=#202124][FONT=Roboto]synclient TapButton3=3 TapButton2=2[/FONT][/COLOR]

---

### Post by LwIh%*7 on 2019-06-03
Will these help?

[https://askubuntu.com/questions/58735/swapping-the-double-and-triple-finger-tap-actions-on-trackpad](https://askubuntu.com/questions/58735/swapping-the-double-and-triple-finger-tap-actions-on-trackpad)
[https://askubuntu.com/questions/999680/libinput-change-touchpad-2-finger-and-3-finger-clicks](https://askubuntu.com/questions/999680/libinput-change-touchpad-2-finger-and-3-finger-clicks)

---

