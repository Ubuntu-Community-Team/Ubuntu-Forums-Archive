---
title: "Videos freezing in ubuntu linux"
date: 2015-03-20
forum: General Help
---

### Post by justin45 on 2015-03-20
I have a dell inspiron 1720 laptop with ubuntu linux 14.04 64 bit version and when I play certain videos, the video freezes and I have to do a hard reboot. The videos freeze either in their original size or in full screen. The affected websites are 
Worldprofit.com
and
various porn sites.

The freezes seem to occur when the video has been playing for a few minutes. What can I do to troubleshoot?

---

### Post by dino99 on 2015-03-20
you might have some usefull warnings/errors logged to help you narrowing down that issue.
be sure that the swap partition is used when playing video (system monitor) and/or check /etc/fstab & 'sudo blkid'

how to do play these videos ? (browser, which one, flash or html5, vlc,...)

---

### Post by justin45 on 2015-03-20
The only browser that I have is firefox. How would I know if flash or html5 is being used? I check on some things and post results later.

---

### Post by pmi2 on 2015-03-20
That is not an especially fast machine, by today's standards... Intel Pentium T2310 / 1.46 GHz, Dual-Core, L2 Cache -1 MB, 64bit, Front Side Bus 533MHz, Mobile Intel GM965 Express Chipset.  Worse, if probably came with 1 Gb RAM, so if that is what you have, I would look into upgrading it to 2 or better 4 Gb.

Not shabby by any means at the time, but video playback and watching flash videos from news sites and such may be somewhat hobbled.

---

### Post by justin45 on 2015-03-20
My laptop was originally a broken laptop. I do computer repair for a living. I have 4 gigs of ram as that is highest amount that the motherboard supports.

---

### Post by plurga on 2015-03-20
have u check this files ? 

[COLOR=#333333][FONT=Arial]/var/log/syslog[/FONT][/COLOR]

[FONT=Courier New]/var/log/kern.log

also , please read this info , it can help u 

[https://help.ubuntu.com/community/DebuggingSystemCrash](https://help.ubuntu.com/community/DebuggingSystemCrash)


[/FONT]

---

### Post by justin45 on 2015-03-20
Here is a photo of the system monitor.

[http://i1270.photobucket.com/albums/jj608/gamekid1/IMG_0718_zpsmcdldrzj.jpg](http://i1270.photobucket.com/albums/jj608/gamekid1/IMG_0718_zpsmcdldrzj.jpg)

It seems that my laptop either freezes and I have to do a hard reboot or I get a black screen.

---

### Post by SeijiSensei on 2015-03-20
> **justin45 said:**
> The only browser that I have is firefox. How would I know if flash or html5 is being used? I check on some things and post results later.

In Firefox, Tools > Add-ons > Plugins.  See an entry for "Shcckwave Flash?"  If not, then run 
```
sudo apt-get install flashplugin-installer
```

---

### Post by pmi2 on 2015-03-20
> **justin45 said:**
> My laptop was originally a broken laptop. I do computer repair for a living. I have 4 gigs of ram as that is highest amount that the motherboard supports.Any computer you can save from the boneyard is a win, :D... Should be more than enough ram!

---

### Post by justin45 on 2015-03-20
I think that I'm just going to hit the brakes on my issue for a good reason. My laptop isn't the best laptop out there. It's also possible that I have hardware failure on my end because of a design issue so I appreciate everyone's help, but sometimes, in laptop repair, there is a point, where a laptop just isn't work fixing.

---

