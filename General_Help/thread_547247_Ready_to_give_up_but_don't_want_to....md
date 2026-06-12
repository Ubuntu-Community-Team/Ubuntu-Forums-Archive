---
title: "Ready to give up but don't want to..."
date: 2007-09-09
forum: General Help
---

### Post by Lujoki on 2007-09-09
Hi...
Yes, I have an ATI Graphics card. I spent all weekend reading up on how screwed they are on Ubuntu 7.04 but also reading that it is possible to get it all working.
I have messed up my xorg.conf several times and fortunately had a backup.

Am I wasting my time?

First thing I'd like to know...
What is a basic command line to know what graphics drivers I am currently using?
Secondly...
After reading instructions on how to create my own driver package which failed for ATI Radeon 9250, if this is a known issue for this why can't I just download the fixed driver and not have to make my own?(For the record the instructions were incorrect as the link wasn't valid) If there is one that someone knows about this can they please show me the way?

---

### Post by p_quarles on 2007-09-09
I don't know which instructions you used, but have you tried this one?:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Anyway, ADM just announced that they are releasing better Linux drivers for their graphics cards in the near future. If you don't want the headache, you might just hold off on Linux until they make those available.

EDIT: Sorry, I also meant to respond to your other question. To show hardware (all of it, including the graphics card):
```
sudo lshw
```

---

### Post by Lujoki on 2007-09-09
> **p_quarles said:**
> I don't know which instructions you used, but have you tried this one?:
[http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

Anyway, ADM just announced that they are releasing better Linux drivers for their graphics cards in the near future. If you don't want the headache, you might just hold off on Linux until they make those available.

EDIT: Sorry, I also meant to respond to your other question. To show hardware (all of it, including the graphics card):
```
sudo lshw
```

Thanks for your feedback... That post does look familiar as I tried several over the weekend.
If I recall the fglrx driver isn't compatible for drivers below 9500, is this true?

---

### Post by p_quarles on 2007-09-09
> **Lujoki said:**
> Thanks for your feedback... That post does look familiar as I tried several over the weekend.
If I recall the fglrx driver isn't compatible for drivers below 9500, is this true?
I wouldn't know, sorry. 

I don't know if you tried this, but there's a script called Envy, written by one of the forum admins, that installs drivers for both nvidia and ATI cards automatically. Worth a shot, at least:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
[http://ubuntuforums.org/member.php?u=19388](http://ubuntuforums.org/member.php?u=19388)

---

### Post by Lujoki on 2007-09-09
> **p_quarles said:**
> I wouldn't know, sorry. 

I don't know if you tried this, but there's a script called Envy, written by one of the forum admins, that installs drivers for both nvidia and ATI cards automatically. Worth a shot, at least:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
[http://ubuntuforums.org/member.php?u=19388](http://ubuntuforums.org/member.php?u=19388)

Thanks, I will give it a try when I get home tonight.
I think I saw the url over the weekend and didn't bother with it because it had the word nvidia in it....

---

### Post by Lujoki on 2007-09-09
If this works is it hard to get dual monitors working and then the 3D desktop etc etc... ?

---

### Post by p_quarles on 2007-09-09
Dual-monitors I don't know about. Desktop effects will be difficult, because the current proprietary ATI drivers are (so I hear) pretty terrible. The new ones, when they come out, should work a lot, lot better.

---

### Post by scxtt on 2007-09-09
i have an ATI X850pro in one computer, i just use the "ati" driver ubuntu ships w/ - desktop effects (compiz) work out of the box (as well as 1600x1200) - when i was using PCLOS, it used "ati" as well and all those effects work too - now i just use the cube and AWN (sometimes snow, sometimes water, sometimes negative) ... not sure about dual monitors, when i was using that i was using fglrx and set it up that way.

---

### Post by w4ett on 2007-09-09
In it's  current form, the fglrx driver is only compatible with the 9500 cards and above. at this time you are stuck with the xorg-driver-ati  See:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I've been trying to find out what cards will be supported by the new ATI drivers (due out in October 2007 ), but haven't found much information as of yet.

Edit: Also see:  [http://ubuntuforums.org/showthread.php?t=543874](http://ubuntuforums.org/showthread.php?t=543874)

---

### Post by Lujoki on 2007-09-09
> **w4ett said:**
> In it's  current form, the fglrx driver is only compatible with the 9500 cards and above. at this time you are stuck with the xorg-driver-ati  See:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I've been trying to find out what cards will be supported by the new ATI drivers (due out in October 2008 ), but haven't found much information as of yet.

Edit: Also see:  [http://ubuntuforums.org/showthread.php?t=543874](http://ubuntuforums.org/showthread.php?t=543874)

When you find out, I'd love to know! :)

---

### Post by Lujoki on 2007-09-10
Envy has failed me. 
That being my last resort, I am forced to give up. Which is a shame because I really liked the look of Ubuntu's interface.

Is there a Linux OS that will recognise my hardware?

---

