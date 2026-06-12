---
title: "Closing laptop makes me lose mouse pointer"
date: 2008-05-05
forum: General Help
---

### Post by poopdog on 2008-05-05
I'm using an HP Pavilion dv6000. 

When I close my laptop lid and then open it back up, my mouse pointer is gone.

I have to move the mouse to the upper-right, watch the power button change colors, then click.  Essentially clicking it blind.

Once it restarts, the mouse is back.

Is there a way around this by chance? 

Thanks

---

### Post by greybit on 2008-05-10
> **poopdog said:**
> I'm using an HP Pavilion dv6000. 

When I close my laptop lid and then open it back up, my mouse pointer is gone.

I have to move the mouse to the upper-right, watch the power button change colors, then click.  Essentially clicking it blind.

Once it restarts, the mouse is back.

Is there a way around this by chance? 

Thanks

I'm having the same problem on my HP Pavilion dv2000 since I upgraded to Hardy.  Does anyone have a solution?  I've tried using rmmod -r psmouse and modprobe psmouse to reinitialize the mouse but this doesn't help...

---

### Post by greybit on 2008-05-14
My cursor doesn't seem to get lost anymore after installing the Nvidia drivers.  Do you have these installed?

In Gnome, go to System -> Administration -> Hardware Drivers.  Once you've entered your root password, you can enable the "NVIDIA accelerated graphics driver."

Hope this helps.

---

