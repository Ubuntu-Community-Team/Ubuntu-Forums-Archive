---
title: "Hardy - NVidia or ATI?"
date: 2008-06-20
forum: General Help
---

### Post by lukemack on 2008-06-20
Hi,

I'm in the process of building a new system which will run Ubuntu 8.04 Hardy. 
I;ve got a laptop running Hardy which has an NVidia graphics chip and am pretty happy with the drivers although multiple screen support is a bit flaky.

I'll need to buy a PCI-E graphics card. Do people recommend ATI or NVidia? Is the ATI support in Hardy as good as NVidia?

many thanks,

Luke.

---

### Post by sdennie on 2008-06-20
Honestly, I would buy something with intel integrate graphics.  If you aren't pleased with the performance after installing and using the machine for a while, *then* go buy an nvidia or ati card.  Intel support is much better than nvidia or ati.

---

### Post by Zorael on 2008-06-20
I don't own an ATI videocard on any of my systems, though I *do* have both Nvidia PCI-E and Intel integrated ones.

In my experience, setting up multiple screens is *very* simple with recent Nvidia *proprietary* drivers, with the TwinView interface. Open up nvidia-settings with superuser permissions, click, click, click, (log out, restart X,) done. If you're going to use the open source **nv** (or **noveau**) driver, this likely doesn't apply. With Intel integrated chipsets you have to manually toil in xorg.conf to get this done, though it's a one-time effort. I'd be glad to be proved wrong; perhaps this is also possible to do while X is running with some RandR command-line command, giving you the same functionality nvidia-setting's TwinView feature supplies.

The intel driver is open source with all the benefits that provides. The nv one is as well, though its composite and DRI support is very limited, if not wholly non-existent. If you want GLX performance, go Nvidia with proprietary drivers. Else an integrated Intel chipset is a very good choice.

I ran WoW with very, very acceptable performance on my Nvidia GeForce Go 7600 PCI-E card on my laptop. Obviously, running the proprietary drivers. Compiz works on my Intel integrated 865G chipset, though performance is a bit lacking. I don't recommend a whole lot of moving and fading effects (wobbly windows, animated expo, window animations, cube), but non-animated expo and other basic features (window tabbing <3) works very well once you disable the animation fluff.

---

### Post by Nepherte on 2008-06-20
I have experience with an Intel GM965 (on board), a Nvidia 7800GT and 8400GS. They all work fine without any problems. If you need a pci-express card, I'd go for an Nvidia one. They work out of the box most of the time and otherwise you will always be able to get it to work with some unorthodox method.

---

### Post by lukemack on 2008-06-20
cool - thanks guys!

---

### Post by isecore on 2008-06-20
I'm running an Nvidia 9600GT and it works great. However for the 9x-series cards you have to manually install the driver yourself which is a bit fiddly if you're not used to Linux.

As for ATI vs Nvidia. I chose the 9600GT because in my experience Nvidia has better driver-support for Linux than ATI. However this is rapidly changing since AMD (who owns ATI) is making a very impressive commitment to providing Linux with decent drivers, documentation and support.

Here's an example I read earlier today of that policy: [http://tech.slashdot.org/article.pl?sid=08/06/19/2113242](http://tech.slashdot.org/article.pl?sid=08/06/19/2113242)

So I guess in a few months time the choice won't be as obvious any longer. Perhaps in a year or so ATI will have overtaken Nvidias place as the obvious choice for linux users?

---

### Post by neurostu on 2008-06-20
So appearently ATI is releasing their newest video card with Linux Drivers.  ATI has decided that they need to provide linux the same support they provide windows.

If I were you  I'd get the intel integrated graphics and wait and see what happens with the ATI linux support 

Here is a reference on the new ATI card: [http://tech.slashdot.org/tech/08/06/19/2113242.shtml](http://tech.slashdot.org/tech/08/06/19/2113242.shtml)

---

