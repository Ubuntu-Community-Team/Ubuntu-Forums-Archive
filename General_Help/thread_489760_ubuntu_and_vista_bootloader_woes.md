---
title: "ubuntu and vista bootloader woes"
date: 2007-07-01
forum: General Help
---

### Post by manitsme on 2007-07-01
hello all
I have a question. I just installed windows vista on this machine , I was dual booting windows xp and ubuntu before that. Now  that I have installed  windows vista the  vista bootloader does not recognize the ubuntu OS. I did find a  program called easy BCD that lets me add entries to it and one is neogrub  but I am not able to  configure it. I was wondering if there was any others that have had this same problem and have gotten it figured out? I thank you all in advance for the help :)
 Thanks MUCH
Steve

---

### Post by jpeddicord on 2007-07-03
The Windows bootloaders are notorious for completely ignoring other OSes on your systems... the only remedy is to make sure you install Vista first, and then Ubuntu overtop of it. :(

Jacob

---

### Post by confused57 on 2007-07-03
> **manitsme said:**
> hello all
I have a question. I just installed windows vista on this machine , I was dual booting windows xp and ubuntu before that. Now  that I have installed  windows vista the  vista bootloader does not recognize the ubuntu OS. I did find a  program called easy BCD that lets me add entries to it and one is neogrub  but I am not able to  configure it. I was wondering if there was any others that have had this same problem and have gotten it figured out? I thank you all in advance for the help :)
 Thanks MUCH
Steve

In case you haven't found a solution, this guide may help:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

You would need to install grub to the root partition, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

