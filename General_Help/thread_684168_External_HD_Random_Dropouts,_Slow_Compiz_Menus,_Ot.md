---
title: "External HD Random Dropouts, Slow Compiz Menus, Other New Issues"
date: 2008-01-31
forum: General Help
---

### Post by bundini on 2008-01-31
Been messing around with Gutsy gibbon over the past few days. A few issues have come up that I've been unable to address:

1. **My external usb hd keeps disconnectin**g randomly. It's like it drops out. Maybe the damn thing decides to go into sleep mode. In any case, the only way that I know of to bring it back up is to disconnect the power and reconnect it.

The unit is a Western Digital MyBook Premium 500gb, NTFS formatted. My fstab reads
/dev/sdb1       /media/disk   ntfs-3g auto,rw,async,exec 0 0

Is there:
[INDENT]a. Some way to rescan my devices? It doesn't appear in /dev/sdb either until after I disconnect and reconnect the power.

b. Some way to keep it from disconnecting? Maybe a periodic disk access to tell it to stay awake and cure it's narcolepsy.
[/INDENT]

2. **Menus are unresponsive** when using **compiz.** IE I click 'Applications' in gnome panel and it takes 2 seconds to respond. With metacity, it's instantaneous. My awn-curves menu also kind of lags and bounces around the screen (I add an item, it moves out of center and kind of sneaks back into place as if it's hoping I didn't notice).

I've got a 7800 gts. I used **envy** to grab and install the drivers from the nvidia site. It's kind of  got some hokey interaction going with the restricted drivers thing. After I install and try to activate compiz for the first time it claims I need to enable the restricted drivers, then when I do that I'm not sure if it tries to reinstall the out of date restricted drivers I'm trying to avoid.

I don't know if I had this problem before (I've installed and done some of these things twice, more on that later). There's kind of a dirty mix of 'free' drivers, restricted drivers, official drivers, xorg configuration utilities, gtk-decorators,  and theme managers out there.

3. File system corruption.

I ran fsck on a mounted partition (it warned me. I thought, like most warnings i.e. 'TOUCHING YOUR REGISTRY MIGHT PERMANENTLY ANNIHILATE  YOUR UNIVERSE' or 'OMFG YOU NEED VIRUS SCANNER', it was safe to proceed anyway). Next few boots and I can't make it pass the loading bar. I use my liveinstall and run fsck and it finds thousands of errors all over the place. After apparently  fixing them things are still toast so I reinstall.

In general the file system seems pretty sensitive compared to NTFS and FAT32 where you can just flip the switch in the back in case things aren't going smoothly and never encounter any problems except with things that may have been saving at the time.

What kind of precautions should I be taking to make sure I don't run into this mess again?

---

### Post by imtheguru on 2008-01-31
1. [http://hardware.slashdot.org/comments.pl?sid=105933&cid=9018042](http://hardware.slashdot.org/comments.pl?sid=105933&cid=9018042)
Research the various s options of hdparm, s 0 prevents disk spindown. Then find a good spot to set the custom hdparm params--perhaps rc.local.

2. What's the question again?

3. fsck can be used in emulation mode with -N. Moreover, the utility posted a clear warning; pay more attention when using tools with increased privileges.

Cheers.

---

