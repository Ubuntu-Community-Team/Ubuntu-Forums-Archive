---
title: "[Ubuntu 14.04] Yet another nvidia issue."
date: 2014-05-29
forum: General Help
---

### Post by Skorm92 on 2014-05-29
Hello Ubuntu Forums!

Yes... yet another nvidia issue/complain thread.
I've installed nvidia in many different ways now but end up with the same result everytime.

Please do not tell me to reinstall ubuntu again since I already re-installed it _**7 times**_ now.. (and counting)

On my last try I installed the nvidia drivers from the official site, using alt+ctrl+f1 to shut down x server and execute the .run package.
And again, black screen only my mouse pointer is showing.

My laptop setup: [link to hardware.info forum]("http://us.hardware.info/productinfo/194670/asus-n550jv-cm068h#tab:specifications")
Graphic card is a GT 750m.

What the hell do I keep doing wrong to end up like this?
I don't know what terminal commands I've been running but 1 thing is sure.. It can't detect display...

I'd like to play World of Warcraft on Ubuntu, so I can leave windows for my GF, and use ubuntu for myself.
But without the nvidia drivers, playing wow is @$!#. 

Please... Please... help me.. It should work in some way or another, right?

Thank you in advance.

---

### Post by hyperreal on 2014-05-29
Hello.  When you boot into Ubuntu, use alt+ctrl+f1 to enter another virtual terminal, and run the command:  "sudo nvidia-xconfig".  This will backup your current xorg.conf file and replace it with one that supports nvidia graphics.  Once this is done, reboot and see if there is progress.

---

### Post by deadflowr on 2014-05-29
Is that card an optimus card?
Perhaps an answer here can help
[http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-bumblebee-nvidia-prime-gt650m-on-ubuntu-13-10-an](http://askubuntu.com/questions/412452/getting-hybrid-graphics-to-work-bumblebee-nvidia-prime-gt650m-on-ubuntu-13-10-an)

---

### Post by Skorm92 on 2014-06-05
Sorry for the late response,
Been on vacation, I'll try the above awnsers and will post feedback/output later

---

### Post by Duncubuntu on 2014-06-05
750m is optimus. For me, proprietary drivers from the repo worked like a charm, enabled the card, and allowed me to still use the HD4000 and switch to the Nvidia when needed. I never use drivers from Nvidia's website as it usually just gives me a headache, or doubles my beer consumption.

---

### Post by buzzingrobot on 2014-06-05
The best way to install Nvidia's drivers is via the "Additional Drivers" tool.  This presents drivers appropriate for your card.  

Installing the driver packaged at the Nvidia site can be problematic, as you've discovered. They package it as a rudimentary compressed tar file with a shell script install.  This works across a variety of Linux distribution but leaves the install invisible to any packaging and dependency resolution tools as well as, typically, leaving it up to the user to re-install after a kernel upgrade (very often noticed when the new kernel boots to a black screen thanks to the now mismatched driver.)

---

