---
title: "[SOLVED] Hardy: No compiz on laptop with ati?"
date: 2008-04-22
forum: General Help
---

### Post by Average Joe on 2008-04-22
I guess I was maybe a bit impatient, but yesterday I decided to upgrade from Gutsy (7.10) to Hardy (8.04 RC).

Two things went wrong (as far as I can tell). First, as always I cannot get my wireless network to work with WPA2 and the Network Manager. Apparently this is not fixed yet. I'll probably need to install Wicd again.

Second, my Compiz effects were gone. I went through the file /usr/bin/compiz and there it says:
```

[...]
#don't run on laptops using ati driver
        if laptop-detect; then
                for DRV in ati radeon; do
                        if egrep -q "Loading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG &&
                           ! egrep -q "Unloading ${XORG_DRIVER_PATH}${DRV}_drv\.so" $LOG;
                        then
                                verbose "Found laptop using ${DRV} driver. \n"
                                return 1
                        fi
                done
        fi
[...]
```
That explains. I happen to have a laptop with an ATI card. Compiz was always worked with it. So why disable it now? So I changed the "return 1" in there into "return 0" and after that I could enable Compiz.

That is probably not the best solution. Does anybody know why Compiz is not allowed to run any longer on laptops with an ATI card? And if there is a better workaround for this?

EDIT:

In the [thread of Rocket2DMn]("http://ubuntuforums.org/showthread.php?t=764633") [RAOF]("http://ubuntuforums.org/showpost.php?p=4831424&postcount=46") came up with a much better solution. Simply do ```
mkdir -p ~/.config/compiz/ && echo SKIP_CHECKS=yes >> ~/.config/compiz/compiz-manager
``` and your troubles are gone. Thanks guys! :)

---

### Post by ossi on 2008-04-25
:) :):)

Strange - exactly the same thing over here. Did what you said and it seems to work. So, whats the reason to do this? There must be one.....

Here you can see my config:

[http://ubuntuforums.org/showthread.php?t=766388]("http://ubuntuforums.org/showthread.php?t=766388")

---

### Post by lkakol on 2008-04-25
Compiz Fusion was not working on my laptop with an ati driver too.  (ATI mobility radeon 9000).  I changed the value in the post and then I was able to enable compiz.  In Gutsy, compiz fusion worked really well, but now after the update to Hardy animations are extremely slow when doing things such as moving windows with wobbly windows enabled, or minimizing and maximizing windows, while other effects like rotating the cube animate really nicely.  Does anyone know what might fix this?

Edit: I just noticed now that even scrolling up and down a webpage in firefox will cause the application to fade to black, and then come back to life after a few seconds.

---

### Post by mt330404 on 2008-04-25
same problem here, had compiz installed and working great in Gutsy, but i upgraded to Hardy Heron yesterday and compiz seems to be disabled (I have an ATI card as well, running on a Sony VAIO VGN-A150 laptop). I see a lot of people talking about going into the compiz scripts and adding "SKIP_CHECK="yes" to /usr/bin/compiz and it works fine. *Where* exactly does that need to be added within the script? I'm not very good with programming or writing/adding to code so your help is very much appreciated.

---

### Post by Rocket2DMn on 2008-04-25
Have a look at this short HowTo to get cards with the open source ati drivers to work with Compiz Fusion - [http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

