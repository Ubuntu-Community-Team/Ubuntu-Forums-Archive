---
title: "Crashing to Log In screen."
date: 2007-02-27
forum: General Help
---

### Post by BlkMagik07 on 2007-02-27
It's me again with yet ANOTHER problem.

The problem now is when I try to view certain screensavers, games (using Wine), and render with Blender 3D, Ubuntu crashes back to the log in screen.  I am almost 100% sure this has to do with the new ATI bleeding edge drivers I installed because this wasn't happening before I installed them.  Are there any other drivers that will stop this problem from occurring while still keeping my system running smoothly?

:confused:

---

### Post by madcow72 on 2007-02-27
Have you tried just going back to the older driver, or does it not perform well enough for you?

I know I'll catch some flack for saying this, but it's made the biggest difference on my computer:  
Switch to an Nvidia card.  They're well supported, very easy to install and configure drivers.

I lasted 7 months on my old ATI cards, (learned a lot about Linux in the meantime), but life is SO much better with my new Nvidia card.

Just my 2 cents.

---

### Post by BlkMagik07 on 2007-02-27
Thank you for the quick reply.

Yes, the older drivers did not perform well enough for me.  Arranging the windows was so laggy with the old drivers; the windows wouldn't smoothly transition but more like... hop around.  Also, the screensavers were very laggy as well with framerates of about 5 - 10 FPS.

I have been thinking about making the switch to an nVidia graphics card for some time now after my ATI card was having problems running all Source based games.

---

### Post by BlkMagik07 on 2007-02-27
Dunno if this is allowed but...

BUMP.

---

### Post by madcow72 on 2007-02-27
Can you say which graphics card your using and some specs?  With frame rates that slow, it doesn't sound like the driver was installed correctly.  What was the output of:
```
fglrxinfo | grep direct
```  Also, are you sure you were using the correct driver for your card earlier?

I used to use a Radeon 9250, 128MB rv280 and had to use the 8.28.8 driver.  No other driver would work.  I would recommend [[COLOR="Blue"]this howto[/COLOR]]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide") to try re-installing if you want to experiment with a non-bleeding-edge driver.

Good luck!

---

