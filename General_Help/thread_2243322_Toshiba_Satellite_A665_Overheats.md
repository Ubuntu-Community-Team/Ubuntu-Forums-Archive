---
title: "Toshiba Satellite A665 Overheats"
date: 2014-09-08
forum: General Help
---

### Post by Andrew_Chesnutt on 2014-09-08
Hi All,

I'm having a problem with the fan in my Toshiba Satellite A665-S6086 overheating. I'm running Ubuntu 14.04. When I boot up, the fans spin up if the laptop is hot but will return to a very slow speed once GRUB takes over. I'm getting temperatures of 85C+ before the laptop finally shuts off to protect itself.

After searching Google, I came up with a post [http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/](http://tuxtweaks.com/2008/08/how-to-control-fan-speeds-in-ubuntu/). Here are my results:

$sudo apt-get install lm-sensors
$sudo sensors-detect
<Reboot>

: Nothing big here.... everything ran as expected.

$sudo pwmconfig

:My results were:

> # pwmconfig revision 6166 (2013-05-01)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.


We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.


/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed


This is as far as I've gotten. Any of the other fixes I've come across haven't worked either. I even went to the extent of reinstalling the most recent version of Ubuntu to see if that might help.

I;ve also installed the Toshiba-specific package (toshset) and that didn't help either. Any help you could give would be greatly appreciate. Thanks.

---

### Post by EuclideanCoffee on 2014-09-08
This can be due to your hardware being infused with Windows software. I had a similar problem with a similar model. After many days of research, I found out that there's really no remedy.

You can install software that monitors the heat, but nothing registers with the fan hardware. Maybe prop it against a small little fan that you can buy online?

---

### Post by Andrew_Chesnutt on 2014-09-08
Hmm, I formatted the HDD as soon as I got it (I hate the Windows 7 that came with it LOL). When I first installed Ubuntu (it was Jaunty if I remember correctly) it worked correctly & I remember thinking how loud the fan was.

Now, the fan will stay on a uselessly slow speed all the time. If I suspend the laptop then start it up again, it will go from uselessly slow to slightly faster at around 75c but that only lasts for a few minutes.

---

