---
title: "Edgy Eft Problem: Application Crash on Launch"
date: 2006-11-21
forum: General Help
---

### Post by Mr.Vitale on 2006-11-21
Hey guys...

I am having a serious problem, my termial, Azereus , and some other applications.

They are just disappearing from the panel after them are launched, and in the  system monitor they aren't running. I restarted the computer as well as just xserver but the problem persists...  I tried some google searches and found nothing but maybe its something obvious i am missing so any help would be greatly appreciated.

--Alex--

---

### Post by taurus on 2006-11-21
Try to run them from a terminal, Applications -> Accessories -> Terminal, so you can see the whole error messages...

```
azureus
```

---

### Post by Mr.Vitale on 2006-11-21
> **taurus said:**
> Try to run them from a terminal...


taurus, that part of what makes this a serious problem for me, i can't even open terminal.. and the same thing happens to the applications when try to open it from application launcher (alt + F2)

Thanks taurus.

--Alex--

---

### Post by taurus on 2006-11-21
You can't even open a terminal by clicking Applications -> Accessories -> Terminal!!!

Did you do anything to your system like playing around with Beryl/XGL or upgrading before all this happens?

---

### Post by Mr.Vitale on 2006-11-21
> **taurus said:**
> You can't even open a terminal by clicking Applications -> Accessories -> Terminal!!!

Did you do anything to your system like playing around with Beryl/XGL or upgrading before all this happens?


Well i was messing with my xorg.conf flie today but while and after that terminal was working....

It just seemed to stop randomly.. i'm not sure when but i know it worked after restarting with my new monitor configurations...

....and its a new install.. just did it yesterday...

---

### Post by taurus on 2006-11-21
Could be a driver for your graphic card?  I think I've seen this problem before here...  What is your graphic card and have you install a driver for it?

---

### Post by Mr.Vitale on 2006-11-21
My video card is a nvidia GeForce FX 5200 256mb PCI

I installed the the 1.0-9629 driver 

how could that affect it though?

---

### Post by taurus on 2006-11-21
What if you edit /etc/X11/xorg.conf and replace the "nvidia" with "nv" and reboot.  See if you can open anything up now!!!

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Mr.Vitale on 2006-11-21
Well it made me have to reconfigure the xserver and unfortunatly it didn't fix the problem

---

### Post by Mr.Vitale on 2006-11-21
Any help would be greatly appreciated.. i am incredably lost here and going absolutely crazy....

crazy enough to boot back into windows... 

thanks taurus... do you have the slightest idea as to what it might be...


I welcome specualation at this point...


--Alex--

---

### Post by taurus on 2006-11-21
I recall somebody had the same problem as yours when he couldn't run anything at all.  Come to find out later that it was because of X, graphic card driver.  Did you have to go through the whole "sudo dpkg-reconfigure xserver-xorg" to reconfigure your X again?

---

### Post by shpook on 2006-11-21
I may be affected by a similar problem. In my case one particular application refuses to start up 100% of the time (kaffeine). And occasionally Adept or Synaptic seem to fail perhaps 3-5% of the time.
They start up, hourglass icon appears in the taskbar, and about 10s later disappears without the application being launched.
Don't think I've had this problem with any other apps though.

---

### Post by Mr.Vitale on 2006-11-21
> **taurus said:**
> I recall somebody had the same problem as yours when he couldn't run anything at all.  Come to find out later that it was because of X, graphic card driver.  Did you have to go through the whole "sudo dpkg-reconfigure xserver-xorg" to reconfigure your X again?


Yep...

When i switched it to 'nv' it used the open source drivers and my dual monitor configuration didn't like that, so i had to work some magic and use the DSL rescue CD, but i managed to boot into Ubuntu, and i had no success..

--Frustrated Alex---

lol

---

### Post by shpook on 2006-11-21
This comment in "Known bugs and workarounds for edgy" seems interesting:

[http://ubuntuforums.org/showpost.php?p=1782426&postcount=62](http://ubuntuforums.org/showpost.php?p=1782426&postcount=62)

The guy is suggesting to use a different kernel as a possible fix to some hardware issues.

---

