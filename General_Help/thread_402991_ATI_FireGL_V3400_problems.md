---
title: "ATI FireGL V3400 problems"
date: 2007-04-06
forum: General Help
---

### Post by sargosis on 2007-04-06
I'm having some serious problems with the fglrx drivers for my video card. I have an ATI fireGL V3400 and i am using xinerama to make my setup dualscreen. unfortunately, the video card drivers appear to not be loading correctly (despite several smooth re-installations). glxgears throws some kind of error on startup and only works on one screen (slowly too). I've talked with some people and they say that my specific card is not supported. i'm really hoping that's not the case, and if anyone could help me out, i'd be appreciative. 

glxgears writes this:
Xlib: extension "XFree86-DRI" missing on display ":0.0".

and fglrxinfo returns this:
Xlib: extension "XFree86-DRI" missing on display ":0.0".
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.5.1) 


let me know if you need any additional information.

---

### Post by sargosis on 2007-04-06
Anyone have any ideas or should i just give up and switch back to windows?

---

### Post by omargohan on 2007-04-10
Hello:

Maybe this can help you:

Using "Feisty Fawn" and "Restricted Drivers" you should have:

*Driver for ATI - "In Use"*

Then you can install beryl easily doing:
[I]
sudo apt-get install beryl[/I]

After that create a new session according to [https://help.ubuntu.com/community/CompositeManager/Xgl]("https://help.ubuntu.com/community/CompositeManager/Xgl")

In order to use Xinerama and ATI (v3400) and Beryl you must open the new session (Xgl), open a terminal and write down:

*sudo aticonfig --drop=horizontal --overlay-on=1*

Tip: --overlay-on can work with 1/0 depending of you screen

And finally:

[I]beryl-manager --no-force-window-manager
beryl-xgl --use-copy[/I]

Listo!!! Your **Xinerama** + **Ubuntu** + **ATI** + **Beryl** should work perfectly...

If you have any questions send me an email at **omargohan** at gmail.com

Also I attach the xorg.conf

Regrets Gohan :p

---

