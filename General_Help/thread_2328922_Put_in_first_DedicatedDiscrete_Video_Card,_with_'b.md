---
title: "Put in first Dedicated/Discrete Video Card, with 'buntu OS's installed or not?"
date: 2016-06-25
forum: General Help
---

### Post by mikodo on 2016-06-25
Hi,

My only machine (Desktop) uses Intel Integrated Graphics. (CPU + RAM). No GPU for HD like Intel i3/5/7. It has support for OpenGL 1.4. I need more graphics. 
[URL="https://us.msi.com/Graphics-card/N720-1GD3HLP.html"]
[/URL][This Discrete/Dedicated PCI-E NVIDIA Card]("https://us.msi.com/Graphics-card/N720-1GD3HLP.html"), will work with my machine and has vendor support for OpenGL 4.4.

I would like to keep my Xubuntu 14.04.1, Xubuntu 16.04.0 and Ubuntu 16.04.0 OS's installed as I have them and, put in the Video Card with the OS's installed.

Can I do that without too much trouble getting the OS's to use OpenGL 4.4 or, is it generally accepted to be "best practice" to do this changing to Video Cards on fresh installs only?

Thank you.

---

### Post by sudodus on 2016-06-25
Often it works directly to add a graphics card. The built-in drivers can manage it. There are exceptions, particularly with new cards, if there is no linux driver, that recognizes it.

nvidia cards (or other brands with nvidia chips) often need the boot option nomodeset to produce some graphic output with the built-in nouveau driver. After that a proprietary driver can be installed in order to get the full performance of the nvidia graphics chip.

-o-

I have nvidia graphics in two computers, I have added a card to a computer with already installed Ubuntu based operating systems, and it works for me. But I have no experience of the particular graphics card that you link to. Let us hope someone knows about that card, and can give advice about it.

---

### Post by sudodus on 2016-06-25
If you want to get an nvidia card, that definitely works with Ubuntu, you can select of the cards, that is used in computers sold by a company, that delivers computers with Ubuntu. I don't say that you should buy from this particular company, that I am linking to, because I think it is not located in your continent, only that you can select one of the graphics cards used by the company. And you can browse the internet for corresponding specs from other companies, that sell computers with Ubuntu and read about successful installed systems at the Ubuntu Forums :-)

[http://www.ggsdata.se/pcmoder/pcdator3.php](http://www.ggsdata.se/pcmoder/pcdator3.php)

cheap: Nvidia GeForce 210
better: Nvidia GeForce GT 610
fancy: Nvidia GeForce GTX 980

(I have an Nvidia Geforce GT 430, which is an old card today, but it works for me.)

---

### Post by mikodo on 2016-06-25
Thank you, sudodus.

All very useful information for me. Reading, reading and learning I hope. :)

Addendum: 

Interesting. [Eight Virtues]("http://www.eightvirtues.com/") who build Linux computers and pre-install Linux OS have two cards they sell the desktop with. The [GeForce GT 610]("http://www.eightvirtues.com/desktops_step_5.html") is one of them! Of course the same card is mentioned in the page you linked earlier. 

Well, I think I'll get the 2GIB silent one. [GT610-2GD3-CSM]("http://www.gigabyte.us/products/product-page.aspx?pid=5067#ov")    Certainly not new but, not that old either. I don't game, I want to use it to test when they get to fixing a [bug ]("https://bugs.launchpad.net/ubuntu/+source/unity8/+bug/1400580")in Unity8. My old integrated graphics worked well with Compiz in 10.04 and could use all its' compositing effects (not sure about 3D) but, does not have the capacity to use all the functions of today, when I tested in Kwin compositor now.

On using                       nomodeset = [Here]("http://ubuntuforums.org/showthread.php?t=1613132") and [Here]("http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu/38782")

Among the many on installing drivers = [Here]("http://askubuntu.com/questions/61396/how-do-i-install-the-nvidia-drivers") [URL="http://ubuntuforums.org/showthread.php?t=1613132"]

[/URL]
Take Care!

---

