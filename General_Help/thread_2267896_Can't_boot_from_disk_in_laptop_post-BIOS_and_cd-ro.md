---
title: "Can't boot from disk in laptop post-BIOS and cd-rom double mounts every disk!"
date: 2015-03-04
forum: General Help
---

### Post by syerra on 2015-03-04
So when I pop in an .iso disc (two different light-weight isos for my 2006 Satellite A100 burnt on two different computers) once Lubuntu starts it tells me that I have a blank disk and two identical icons are on my desktop. 

My /etc/fstab doesn't have a cd-rom automounted, just my hdd and swap.
I tried boot-repair and I still can't run an iso CD
the funny thing is when I insert an audio cd it'll still double mount but if I start Audacious and click on play CD no probs, I get to read it perfectly.

Any ideas? I've spent all afternoon searching the interwebs and no luck.

Thanks

---

### Post by oldfred on 2015-03-04
Can you boot from flash drive?
I have Toshiba A105 from end of 2006 and it gives me the option to boot from flash drive, so that is now how I install to it.

What tools did you use to burn ISO to disk?

This has links to install procedure, but is Ubuntu not Lubuntu. Procedure would be the same.
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

        [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by syerra on 2015-03-04
Thank you for your response but I'm no newbie to linux. The prob isn't the iso, it's the double mounting. those same iso cds run fine on my other computers. I've checked my BIOS and the CD-DVD drive is the first in the boot priority, it just won't load the cd. Once Lubuntu is up the same iso shows up as blank disk, twice! I'm completely perplexed. I've found nothing useful searching with the keywords I'm using. I had never seen this problem before...

---

### Post by oldfred on 2015-03-04
I have not booted CD on old laptop for ages, but what does f12 show as boot options? I get hard drive and USB flash drive.

---

### Post by syerra on 2015-03-04
Yeah, I get four options of which the CD drive is included but the reader reads it as a blank cd...

---

### Post by oldfred on 2015-03-04
Try cleaning lens, not easy to do as it is back inside system. Sometimes that helps.
They used to have disk cleaners, but all they were, were a small brush on CD to remove dust.

---

