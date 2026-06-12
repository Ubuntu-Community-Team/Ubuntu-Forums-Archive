---
title: "Temp Question"
date: 2007-10-10
forum: General Help
---

### Post by Imsati on 2007-10-10
Not sure where I should post this, but here goes.

I am using SpeedFan and PC Wizard to monitor system temps. PC Wizard seems to read the same temps as SpeedFan, but labels them wrong. What program do I believe? PC Wizard says my CPU temp is 10*C lower thatn wqhat SpeedFan says it is. When I assigned that label to SpeedFan, I opened a few programs, then saw what temp went up the quickest and assumed it was the CPu. Here's an image:

[[IMG]http://img225.imageshack.us/img225/3686/tempscreenshotye4.th.png[/IMG]](http://img225.imageshack.us/my.php?image=tempscreenshotye4.png)

PC Wizard also lists my CPU fan at 10 rpm. Other than BIOS (which lists at full CPU speed), is there a way to get a 'real' reading of CPU temp at idle when it's cut back using EIST?

---

### Post by expatCM on 2007-10-10
Presumably you are running these Windows programs under Wine?

If you run any of the Ubuntu monitoring tools are the readings any better?

---

### Post by Imsati on 2007-10-11
Heh, no, sadly. This is on my XP disk. My Ubuntu drive died during a routine computer maintainence (after 6 years of fiddling, I finally fried my first HDD!) because I forgot to kill the power.

My replacement drive will be here tomorrow and I expect to have Feisty loaded up 20 minutes after it does, so I'll check then. Do you have a recommendation as to what to use in Feisty to monitor it? I know about a KDE version, but not one for Gnome.

--Jay

---

### Post by expatCM on 2007-10-11
I guess a lot will depend on exactly what you want to accomplish.  Remember that most versions of BIOS have some basic system health monitoring built in which does make like simple.

gdesklets has a range of related applets which you may like to install.

hddtemp is another gnome based utility which ....  monitors the hdd.

There are things like sensors applets which like the above you will find in the repositories.

Not everything will work for you, it will depend on which sensors are supported by your motherboard and hard drive. 

And there is of course Conky which will give you hours of fun just setting it up to do what you want and it can do lots and lots ...
[http://conky.sourceforge.net/](http://conky.sourceforge.net/)

---

### Post by Imsati on 2007-10-11
Holding at 31*C now at idle, so all is good. I use kdesklets for Kubuntu and I like it, so it's good to know there's a Gnome version too. I'll go with that one once everything is up and running again.

Thanks!

---

