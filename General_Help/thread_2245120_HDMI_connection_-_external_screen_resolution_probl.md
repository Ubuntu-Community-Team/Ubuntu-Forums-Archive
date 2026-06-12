---
title: "HDMI connection - external screen resolution problem"
date: 2014-09-21
forum: General Help
---

### Post by Pelvur on 2014-09-21
I have resolutionproblems when connecting my Dell Precision M4400 laptop to my SamsungHDTV through HDMI. Actually, my laptop does not have HDMI port, butit has DisplayPort, and I have a cable DisplayPort-to-HDMI. 
The laptop hasnVidia card Quadro FX770M that uses nVidia binary driver  - version331.38 from nvidia-331 (proprietary, tested).
First, when TV isconnected, its native resolution (1360x768) is not recognized.1920X1080 is offered by default. The screen is recognized as 7”screen (it is actually 37”), but that bothers me the least.

[[IMG]http://s18.postimg.org/4c95mkbad/image.jpg[/IMG]]("http://postimg.org/image/4c95mkbad/")


What really bothers me is that the TV screen does not show full picture. This is how the full picture (nvidia settings window) look on my laptop screen.

[[IMG]http://s27.postimg.org/3sgl3osz3/image.jpg[/IMG]]("http://postimg.org/image/3sgl3osz3/")

And that is how it looks on the TV screen.

[[IMG]http://s4.postimg.org/vchdjkq6h/3_1.jpg[/IMG]]("http://postimg.org/image/vchdjkq6h/")


By trial and error,I found certain nvidia screen settings that allow me to see full picture on my TV screen. 

[[IMG]http://s29.postimg.org/rudr42d9v/image.jpg[/IMG]]("http://postimg.org/image/rudr42d9v/")

I suspect that aspect ratio may not be perfect but it's not too bad. The problem is, whenever I disconnect the TV screen, or even simply turn it off and on, I have to changethese setting again. It doesn't come back to default, but it saves it differently from what I have in current settings. 

[[IMG]http://s30.postimg.org/k09sspgnh/image.jpg[/IMG]]("http://postimg.org/image/k09sspgnh/")

So I have to manually change settings to what is desirable and then click Apply. and I do it every time I reconnect the TV screen or turn it on/off.

I tried to save settings to X configuration file, tried to merge and save without merging; I tried to manually adjust the  X configuration file, and nothing helped.

Can anyone help me here to make correct setup? What I'm trying to achieve is that I make the setup once, and works properly each time I connect the TV screen.


As a side note, VGA works perfectly, recognizes my TV screen resolution properly (although defines it as 40” instead of 37”). But I prefer to have one cable instead of two.

---

### Post by Pelvur on 2014-09-23
So based on what I can see in xorg.conf file, each time I reconnect HDMI monitor, the metamode I setup manually is removed, and default one is applied. Does anyone knows how to fix the manual metamode so that it is not reset each time? And how btw to add new metamode to the nvidia settings (I have 13 metamodes there, only one is for two screens, and most of them I don't need at all; they probably come default).

---

### Post by Pelvur on 2014-09-26
Well, it seems like I have to give up and use VGA + audio cable instead of HDMI. Besides, the free image host I used to place my pictures deleted most of it. Need to find more reliable one :)

---

