---
title: "Display problem"
date: 2014-02-03
forum: General Help
---

### Post by p2ranger on 2014-02-03
I've been trying to install Ubuntu on a USB drive on my mac, which has been its own hurdle. Now that I have it running, I have this display problem.
[ATTACH=CONFIG]250061[/ATTACH]

As the picture of the screen shows, once the desktop comes up, it shows 4 ubuntu desktops which are all the same. The mouse pointer shows up on all 4 at once and clicking on anything produces the same result simultaneously in each desktop. The text is also very difficult to read. Thankfully I knew where to click for reboot/shutdown, because that's all I can really do with it at this point. I'm assuming this must be a display driver issue. Any ideas?

Ubuntu 13.10
iMac 2009
12 Gb RAM
ATI Radeon HD 4670

This is essentially just the live CD iso on a USB drive that is running. I tried opening the terminal and doing: sudo apt-get update and sudo apt-get upgrade, but the results in the terminal are not readable just like any text on this.


Thanks

Jason

---

### Post by bc.haynes on 2014-02-03
I assume this is one monitor in the thumbnail? It looks like the Workplace Switcher. Have you tried double-clicking on the upper left desktop. Long shot.

---

### Post by Mark Phelps on 2014-02-04
> I'm assuming this must be a display driver issue.

While that might be the case, sorry to tell you, but you're stuck using the default Radeon driver that is already installed.

AMD dropped Linux driver support for your video card last summer.  So, there are no AMD drivers you can download that will work with that card and any version of Ubuntu newer than 12.04.1.

---

### Post by p2ranger on 2014-02-05
Thanks for the info. I had found where I thought that it was supported:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

I guess not. I have tried using Xubuntu and Ubuntu 12.04.01 and even 10.10, but I get he same results with the 4 desktops.

Any chance that if I tried something like arch would it be able to work or is there just no chance that there would be a display driver to work with my computer on any kind of linux

Thanks

Jason

---

