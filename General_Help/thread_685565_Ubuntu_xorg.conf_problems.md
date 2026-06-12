---
title: "Ubuntu xorg.conf problems"
date: 2008-02-02
forum: General Help
---

### Post by motonoodz on 2008-02-02
[FONT="Verdana"][SIZE="2"]Hello,

I'm new to Ubuntu but have been using Unix on and off for a while.

I'm dual booting my machine with MCE by selecting the boot disk at start-up. They are installed on separate disks.

Anyway, I'm having problems with Ubuntu during boot where following the initial Ubuntu splash screen I get a blank screen.

Both MCE and Ubuntu have been newly installed in the last couple of weeks and both have been working fine.

However since upgrading and playing around with the display drivers in MCE, Ubuntu now fails to load, exhibiting the symptoms detailed above. I have since regressed the drivers.

I have tried reconfiguring xserver using various combinations of the defaults and the monitor manufacturer spec using **sudo dpkg-reconfigure xserver-xorg**

I also tried a backed up xorg.conf from running the live CD previously which also failed to make any difference.

xorg.0.log doesn't seem to show any obvious errors.

Finally, trying the safe graphics mode on the live CD also fails although I get an error indicating xserver has failed 6 times in the last 90 seconds.

Any suggestions as to what the problem could be would be great!

Thanks[/SIZE][/FONT]

---

### Post by jken146 on 2008-02-02
What graphics card do you have?

---

### Post by motonoodz on 2008-02-02
It's onboard; Mobile Intel® 915GM/GMS, 910GML Express Chipset Family

Thanks for the quick response!

---

