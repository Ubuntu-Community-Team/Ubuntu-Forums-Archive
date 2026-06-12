---
title: "Logitech VX Nano Wireless Mouse Not Working"
date: 2008-06-30
forum: General Help
---

### Post by party1421 on 2008-06-30
I just installed Hardy a couple weeks ago and yesterday when I plugged in my new VX Nano nothing happened.  The trackpad on the laptop still works, but the VX Nano doesn't do anything.  I haven't found anyone else on the forums who has a similar problem, so if anyone could give me some tips it would be much appreciated.

---

### Post by steveneddy on 2008-06-30
Isn't this a bluetooth mouse?

---

### Post by party1421 on 2008-06-30
No, it's not a bluetooth mouse

---

### Post by steveneddy on 2008-06-30
Um, ok....

did you try fresh batteries?

Just trying to help.

Try a different USB port on the PC to see if it works better there.

---

### Post by Musky Melon on 2008-07-11
My Logitech VX mouse doesn't work either. It used to work automagically but then one day it stopped working. I used to have to fiddle with the receiver to get it to work again by jiggling it around so I though it was the receiver that went bad (I tested the USB ports on my laptop and they work fine). However now neither the old or new receiver work. It could be the mouse itself although it could easily be Ubuntu as well.

---

### Post by Crath on 2009-09-02
I know this is an old thread but I am having the same issues.  I had Win7 installed on my netbook (hp mini 1000) and my logitech vx nano worked just fine.  I installed ubuntu desktop on it and it doesn't seem to recognize it.  Trackpad still works fine though.

Google didnt really help with finding a clean cut way to get it working, just people fixing the buttons.

Any help is appreciated! thanks.

---

### Post by starrlight on 2009-09-14
hello i am having the same problem with my logitech vx nano mouse i installed it on xp vista and ubuntu 3 months ago and it was working fine on all three untill 2 days ago. now the cursor responses are sluggish as heck. i've changed to fresh batteries but no luck. is there any one at all that can help fix this?

---

### Post by Vakman on 2009-09-14
> **starrlight said:**
> hello i am having the same problem with my logitech vx nano mouse i installed it on xp vista and ubuntu 3 months ago and it was working fine on all three untill 2 days ago. now the cursor responses are sluggish as heck. i've changed to fresh batteries but no luck. is there any one at all that can help fix this?

Let us take a look in the Xorg, post the section called "InputDevice" and let's see what we have.
```
gksudo gedit /etc/X11/xorg.conf
```
To open Xorg. What I was planning on saying is probably going to help Crath more, so do the same Crath. Seeing how your mouse has never worked.

---

### Post by sr20ve on 2010-01-13
I'm having the same problem, I thought the mouse was bad until I finally tested it on an XP machine and after I installed the Logitech software it worked. So how can I get this working in Ubuntu? I'm running 9.10 UNR. Any thoughts?

---

### Post by ajpaverd on 2010-05-19
Just for the record on this one - my Logitech VX Nano worked with Ubuntu 9.10 and now with 10.04. I does not have all the button functionality but the scroll wheel and back and forward buttons work.

I haven't done any customisation of Ubuntu - I just worked straight out of the box. I would also recommend testing your mouse on Windows (with the Logitech SW) if it isn't working.

---

### Post by sr20ve on 2010-05-24
Sorry I never posted back with my fix...

I'm really not sure of the circumstances to why this worked, but this mouse did not work for me in Ubuntu out of the box. I had to install the software and pair the devices on an XP machine, after that, it worked fine in Ubuntu and I have not had any further problems. I have since used it on different Ubuntu versions and on different computers.

I suspect (although untested) that if you don't use it for a long period of time, the mouse and receiver may lose sync and need to be re-synced from a windows box, hence why it did not work when I first received it.

---

### Post by ottabaub on 2010-07-12
> **sr20ve said:**
> Sorry I never posted back with my fix...

I'm really not sure of the circumstances to why this worked, but this mouse did not work for me in Ubuntu out of the box. I had to install the software and pair the devices on an XP machine, after that, it worked fine in Ubuntu and I have not had any further problems. I have since used it on different Ubuntu versions and on different computers.

I suspect (although untested) that if you don't use it for a long period of time, the mouse and receiver may lose sync and need to be re-synced from a windows box, hence why it did not work when I first received it.

My Logitech nano worked fine with 8.04, 9.10 and 10.04 when I upgraded from 9.10 in May. I recently bought a Asus netbook that runs Windows 7. Yesterday I unplugged my nano receiver from my laptop (that was turned off) and plugged it into the netbook. Worked fine. This morning I plugged the nano back into my laptop and it doesn't work anymore. I tried new batteries. No joy. I plugged it into a desktop PC running Windows XP. Worked fine. Back into my laptop - still doesn't work.

I don't know what to do. Makes no sense to me.

---

### Post by ottabaub on 2010-07-12
> **sr20ve said:**
> Sorry I never posted back with my fix...

I'm really not sure of the circumstances to why this worked, but this mouse did not work for me in Ubuntu out of the box. I had to install the software and pair the devices on an XP machine, after that, it worked fine in Ubuntu and I have not had any further problems. I have since used it on different Ubuntu versions and on different computers.

I suspect (although untested) that if you don't use it for a long period of time, the mouse and receiver may lose sync and need to be re-synced from a windows box, hence why it did not work when I first received it.

My Logitech nano worked fine with 8.04, 9.10 and 10.04 when I upgraded from 9.10 in May. I recently bought a Asus netbook that runs Windows 7. Yesterday I unplugged my nano receiver from my laptop (that was turned off) and plugged it into the netbook. Worked fine. This morning I plugged the nano back into my laptop and it doesn't work anymore. I tried new batteries. No joy. I plugged it into a desktop PC running Windows XP. Worked fine. Back into my laptop - still doesn't work.

I don't know what to do. Could using it with Windows 7 have rendered it useless for Ubuntu? Makes no sense to me.

---

### Post by yours-truly on 2011-07-11
> **sr20ve said:**
> Sorry I never posted back with my fix...

I'm really not sure of the circumstances to why this worked, but this mouse did not work for me in Ubuntu out of the box. I had to install the software and pair the devices on an XP machine, after that, it worked fine in Ubuntu and I have not had any further problems. I have since used it on different Ubuntu versions and on different computers.

I suspect (although untested) that if you don't use it for a long period of time, the mouse and receiver may lose sync and need to be re-synced from a windows box, hence why it did not work when I first received it.

Thanks.

I've tried to get it work on three different ubuntu machines with no luck.
Than i read this post, started xp in a virtual machine, waited for the driver to finish loading, unplugged mouse , went back to an ubuntu laptop, plugged in an it works like charm.
Even though, it shows no bluetooth device icon ... 

So I restarted the machine, with the nano dongle in the machine.
Works, but no BT Icon.

I've unplugged the dongle, put it in the mouse (it turns off)
Shutdown laptop. Started all and plugged dongle in, and it works. But no BT Icon.

Last Test, removed the Batterys for 30 Seconds, the dongle, and Restart.
Everything works fine. But no BT Icon.

So thanks again, your Post was right. One Connect through winXP after a long time of no use is enough to get it working again. This Mouse is no BT Device in Common Sense. It only works with the original Logitech BT Dongle.

With nice Greetings, 
yt

---

