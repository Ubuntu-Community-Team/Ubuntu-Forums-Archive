---
title: "cd/dvd rom"
date: 2007-01-07
forum: General Help
---

### Post by lindberg.bill on 2007-01-07
I was trying to install dual monitors, no use there, but any way once I was stuck in a black screen and in desperation I tried a combination of ctrl, alt, delete, backspace, and various F#'s (F1, F2, F3, F4, F5 etc) I think I tried them all and all combinations.  I have no idea if this is what trigered the problem because I was also gediting my xorg.conf file.  Now I have to cd or dvd rom.  I dual boot xp professional and they are not there either.  As a matter of fact there is some type of error that pops up when I boot up now but it flashes so fast all I can see after the hard drives load is "errror log..." I guess this might not be an ubuntu problem, but I think it seems to much of a coincidence, obviously I'm no expert.  Well I apreciate any help you have to offer. :-D

---

### Post by bodhi.zazen on 2007-01-07
Ouch ....

I am not sure I can help much, but if you are having problems with your CD ROM/DVD in multiple OS it sounds like a hardware problem ....

I can not see the relation between the two (editing xorg.conf and your DVD).

If you want to fix your Ubuntu install, boot to the recovery mode. This should boot to the CLI (command line interface)

enter:```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You should be able to boot to a gui now .....

As far as Dual monitors, it depends on your video card, start here ....

 [http://doc.gwos.org/index.php/DualMonitors](http://doc.gwos.org/index.php/DualMonitors)

Although there are also how-to's in the forums ....

Let us know if we can be of further assistance ...

---

### Post by lindberg.bill on 2007-01-08
They are up and running again and I don't know why, however, I did run a mem test as it seems only almost to completion 12 hours plus time running. :confused:

---

