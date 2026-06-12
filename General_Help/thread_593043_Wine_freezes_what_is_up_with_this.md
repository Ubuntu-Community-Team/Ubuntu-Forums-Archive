---
title: "Wine freezes what is up with this?"
date: 2007-10-26
forum: General Help
---

### Post by nu2this on 2007-10-26
Ok I have Gutsy on a 32 bit machine I have installed wine through apt-get. Now the not so fun part
when type in winecfg in terminal I get this:
"wine: creating configuration directory '/home/user/.wine'..."
Then my system freezes needing a reboot to get out of it. It also does this when I do Applications>Wine> Configure.
What is wrong with this?  I've not ever had anything like this! What fix is there? I've tried Uninstall/re-install removal of the .wine folder. I'm out of ideas.

---

### Post by mfratus2001 on 2007-11-01
I had just upgraded to Gutsy from Feisty. Wine was working before. 
Motherboard: KM400-M2 using UniChrome S3 drivers. Now Wine locks up.
After reading tips that didn't work, I went to the ECS motherboard site to get a newer driver.
Their newest driver was Feisty. I forced the driver install by creatve editing, and it killed my X windows.
Startx complained it was missing the driver, which I suppose got deleted.
So I got the Feisty via driver from /usr/lib/xorg/modules/drivers on the live CD (I was ready to install Feisty over Gutsy) and tried that on my installed system. It worked!

So, I guess the Gutsy Via driver is the problem. If  you try this and it doesn't work, I'll look at my xorg.conf and show that.
I messed up and killed my X Windows, but fixing that fixed the wine lockup problem.

Good luck.

Mike.

---

