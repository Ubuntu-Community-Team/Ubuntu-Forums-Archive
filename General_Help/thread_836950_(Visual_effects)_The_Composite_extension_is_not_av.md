---
title: "(Visual effects) The Composite extension is not available"
date: 2008-06-22
forum: General Help
---

### Post by Starlance93@hotmail.com on 2008-06-22
I have just installed Ubuntu 7.10 on my Asus laptop. I have not been able to get the "Visual Effects" working.

My laptop:
Asus F5R
ATI Radeon Xpress 1100
Intel Pentium dual core 1.86 Ghz
884 Mb RAM

What is happening is I go try to enable visual effects and it gives me the message "The Composite extension is not available"
I have gone to this page ([https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)) and followed the instructions there. It said that Compiz was in fact installed.
Before I installed the restricted driver for my ATI card it gave me the error message that it could not be enabled.
Might my problem be that Compiz is not compatible with my card?

Thank you in advance to anyone willing to help.

---

### Post by Fingers &amp; Thumbs on 2008-06-22
So you have your ATI driver installed, is it enabled? You can find this at >System >Administration >Restricted Drivers (or Hardware Drivers).

---

### Post by Starlance93@hotmail.com on 2008-06-22
It says:
ATI accelerated graphics driver      (checkmark for enabled)      In use


I also have another thing in the restricted drivers section. Firmware for Broadcom 43xx chipset family. I enabled this and it disabled my mouse use and a few other things so I disabled it.

---

### Post by Fingers &amp; Thumbs on 2008-06-22
Ok, the next question, has your computer been restarted since the driver was installed/enabled, I'm guessing so you should have been prompted to do so.

In >system >preferences >appearances, go to the "Visual effects" tab, you should see 4 options there, if not you will need to open a terminal and type...

```
sudo apt-get compizconfig-settings-manager
```

or alternatively find it in synaptic package manager if you prefer using a GUI.

---

### Post by Starlance93@hotmail.com on 2008-06-22
Yes. It provides the options: 
None
Normal
Extra
(and I installed an advanced desktop effects settings) Custom

It also gave the same results before installing the extra preferences so that being the problem is ruled out.

It is on None and if I try to select any it says: "The composite extenstion is not available"

And yes I have restarted several times since disabling and enabling those driver/firmwares

---

### Post by Fingers &amp; Thumbs on 2008-06-22
Sorry fella, I think the problem may be beyond me, or perhaps I'm just not focused due to it being 7am here and I'm still awake after a night on the brandy :))

 I'll have a bit of a dig though, if I come up with any useful info I'll get back to you.

---

### Post by Starlance93@hotmail.com on 2008-06-22
Haha Well thank you very much.
Do you think it could be an compatability problem?

---

### Post by Fingers &amp; Thumbs on 2008-06-22
AH, her you go, this guy has the same graphics card as you, and it seems this thread got it working.

[http://www.linuxquestions.org/questions/linux-newbie-8/desktop-effects-could-not-be-enabled-ati-radeon-xpress-1100-compiz-635139/]("http://www.linuxquestions.org/questions/linux-newbie-8/desktop-effects-could-not-be-enabled-ati-radeon-xpress-1100-compiz-635139/")

---

### Post by Starlance93@hotmail.com on 2008-06-22
Thank you very much friend :-) I'll have a look at that

---

### Post by Fingers &amp; Thumbs on 2008-06-22
Something else I've just found out about: [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/article/pages/Compiz-Check")

This will apparently check your system for compatability, and report back any issues that may prevent compiz from working.

---

