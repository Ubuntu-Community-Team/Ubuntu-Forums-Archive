---
title: "Installing a new video card (GeForce 6200)"
date: 2007-04-20
forum: General Help
---

### Post by mjpatey on 2007-04-20
I'm getting really tired of my old ATI card in Ubuntu, so I'm switching to an inexpensive but much more modern nVidia-based card.  It's a PNY GeForce 6200 with 256 MB, with AGP interface. (And yes, my ATI card is actually a lot older than that!)

What, exactly, do I do to make this happen smoothly?

My hope is to turn off the computer, swap cards, turn it back on, and Ubuntu will happily recognize the new card (and compliment me on my good taste).  Screen resolution will be exactly what it was set to before the swap, only now everything will run smoothly.

Can I expect that scenario with the card I've chosen?  Is there anything I'll need to do driver-wise?  Is there anything I'll need to do (before or after the swap) to the dreaded xorg.conf?

Thanks for any help you may have!

-Mark

---

### Post by spankymasterc on 2007-04-20
no... it will detect the card but i think you are going to have to reinstall drivers....

since Ati and Nvida are completely diff companies so diff drivers 

but expect EASY installation for nividia since ati is much much more harder....

if in the worst case scenario u cant get into visual and only text mode

run this

sudo dpkg-reconfigure xserver-xorg

and if it doenst look it here :
[http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu:Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

good luck

:::Cheers:::

---

### Post by dhuff on 2007-04-25
In [another thread]("http://ubuntuforums.org/showthread.php?t=355699"), dpmcoy wrote:
> I swapped out my ATI Radeon 9550 last week for a new Nvidia Ge Force 7600.

It was a lot easier than I expected.

To be perfectly safe, I ran "dpkg-reconfigure xserver-xorg" and reset my video card type to "vesa". I turned it off, replaced the card, and rebooted. Once I did that, I installed the new Nvidia beta drivers through the instructions on one of the forum posts. I restarted the xserver, and everything has been working beautifully since.

---

