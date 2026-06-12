---
title: "Do I need a newer Video board or is there a fix?"
date: 2014-06-15
forum: General Help
---

### Post by held7over on 2014-06-15
My computer is a HP Pavilion Media Center M8000N Dual AMD Athlon 64bit CPU 5600+  2.6Gz
The Graphics Board is a:  NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)

I am trying to install Ubuntu 14.04. Sometimes I can see the Installer and sometimes during the install process the screen suddenly twists and all I see is diagonal garbage on the screen and I have to start over. If I luck out and actually get it installed, the same thing happens on or a bit after bootup!  Is this indicative that my hardware's Video Graphics is just too old? Or is there something else I need to adjust in order to fix this?

If this is caused by the video graphics being too old, what board would be new enough to keep me running for this version of ubuntu and the next one.... but yet old enough to be purchased used on ebay or amazon? I am a bit lost when it comes to video boards.

Thanks! ;)

---

### Post by grahammechanical on 2014-06-15
How much video memory does that card have? That is an important point. Does the live session run? The live session uses an open source video driver that is called Nouveau when used for Nvidia cards.

You could try running the installer using the nomodeset option.

At the first purple screen press Enter and at the next screen press Enter again to set English as the default language. At the screen that offers Try Ubuntu - Install Ubuntu press F6. A small menu will appear at the bottom left of the screen. Select nomodeset and press Enter. Then press Esc to get back to the Try - Install screen and take it from there.

Do not tick "Install third party software." That will install the Nvidia driver. But Nvidia has a habit of dropping support for old cards from its drivers and Ubuntu will install the latest driver. Which may not support that video card.

See how that goes. As regards video cards a lot depends upon whether the motherboard supports PCI and also PCI-Express. If the board supports PCI-Express then look for a PCI-Express card with 500 MB to 1 GB of its own memory. 1 GB memory is what you should be aiming for.

Regards.

---

### Post by held7over on 2014-06-16
Thanks for your reply grahammechanical!

I found the specs on my computer. To the best that I can tell, here is what it says:  Nvidia GeForce 6150SE Graphics with TurboCache (whatever that is), 128MB dedicated Graphics Memory, up to 399MB total available graphics memory as allocated by Windows Vista.

I have no idea of how or if linux allocates graphics memory (but I would assume it must), but it sounds like I am a tad short of memory if 500MB is the minimum I currently need, and 399 is the total that can be available, unless I am misunderstanding and the 128 dedicated and the 399 allocatable are actually added together to make 527MB total....in which case I am 27MB above the minimum entry level...

The live sesson sometimes boots up fine and other times not, quite often the screen goes squiggy a little way into it. I had found the "nomodeset" mentioned in the release notes and have tried that. But maybe I did something wrong in setting it up. I certainly have been ticking "Install third party software", so, evidently that is a certain mistake I have been making.

---

### Post by LastDino on 2014-06-16
I can't speak about the card itself, but even on my on board 128MB graphics Ubuntu works fine. However, you will have trouble running 3d Unity and high level eye candy effects. Same goes for Gnome.
So, whether you want to upgrade or not is up to you.

I would definitely try installing without ''3rd party' enabled and see how things go.

---

