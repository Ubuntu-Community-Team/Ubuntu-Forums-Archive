---
title: "Laptop Upgrade"
date: 2016-03-08
forum: General Help
---

### Post by Sailing_Nut on 2016-03-08
Hi all!

I currently run Ubuntu from an external SSD on my work laptop when I am on the road. (Company policy doesn't allow installing games etc. on the internal HD.) I'm getting ready to have my laptop refreshed and wanted to know if I'll need to re-install Ubuntu on my external SSD or not.

I know that Windows binds itself quite tightly to the hardware and that (without using advanced tools like sysprep) you can't make a dramatic switch in hardware. I have heard that Ubuntu (and Linux in general) is much more forgiving in this respect.

I want to know what (if anything) I need to do / can do to help make the transition go smoothly.

Thanks in advance!

---

### Post by QIII on 2016-03-08
Hello!

Linux is not bound in the same way to specific hardware as current versions of Windows.  That is, you can (in general and with some provisos) move a disk with an installation of Linux from one machine to another.  However, it is possible that you may encounter some frustrations with the very newest and most cutting edge of hardware.  That's pretty rare, but it does sometimes happen.

If you do just a couple of things beforehand, in most cases will probably be fine.  But there are few guarantees in life.

First and always:  ***Back up you important files***.  

Then un-install any proprietary drivers you may have installed.

If you have problems, come back here and I'm sure that we'll be able to help with just about any difficulty.

---

### Post by Sailing_Nut on 2016-03-08
Thanks!

That's what I thought I had heard in the past, so good to confirm it. (More from a trusting my memory point. :P)

I have not installed any proprietary drivers (to my knowledge) so I should be good to go! YAY!

---

### Post by ajgreeny on 2016-03-08
Be a little careful if during your original installation you chose to both update during the process, and also install third party packages; that may have installed a graphic card driver and you might be unaware of the fact.

---

### Post by Sailing_Nut on 2016-03-08
What would be my best way of checking for a proprietary video driver?

And if I have one the best way to uninstall? (apt-get -remove?)

---

### Post by coldraven on 2016-03-08
> **Sailing_Nut said:**
> What would be my best way of checking for a proprietary video driver?

And if I have one the best way to uninstall? (apt-get -remove?)

Press the Dash button (Winkey) and start typing "additional". You'll see the "Additional Drivers" icon appear. Click that and wait a while, any loaded drivers will appear.

---

### Post by HermanAB on 2016-03-08
It may be a good idea to change your graphics driver to something generic before you change the laptop, e.g. VESA.  Otherwise, you may get a black screen if the installed driver won't work with the new hardware.

---

### Post by Sailing_Nut on 2016-03-08
Just checked and I'm using the Nouveau driver from xorg. I'm assuming that is fairly generic. Is that a bad assumption?

---

### Post by ajgreeny on 2016-03-09
No, it is the driver you should be using I think.  If you were using the proprietary drivers they would be named nvidia-### or similar, as far as I'm aware.

---

