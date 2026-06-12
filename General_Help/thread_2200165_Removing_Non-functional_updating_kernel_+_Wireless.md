---
title: "Removing Non-functional updating kernel + Wireless issues"
date: 2014-01-17
forum: General Help
---

### Post by mknudsen84-e on 2014-01-17
Hi all, 

I had been having intermittent issues with my wireless connectivity when using Ubuntu (any version up to and including 13.10). Seems the wireless will just cut out every now and then, and the only way to fix it is to yank out my wireless USB (**Linksys AE1000**) connector and re-attach. 

I made what turned out to be the ill-advised decision to update my kernel to see if that would solve the problem (from **3.11.0-12-generic** to **3.12.0-031200-generic**). 

...Unfortunately, instead of a half-way working wireless, this left with me *no* working wireless at all. 

So, I reinstalled Ubuntu 13.10. But, this has left me with some lingering problems. Ubuntu will not successfully boot at all into its now default Kernel choice in GRUB:  **3.12.0-031200-generic**. It gets to the log-in screen and then freezes. The OS will only work properly if I go into** Advanced Options** and boot it into **3.11.0-12-generic**. 

Glass half full, Ubuntu is working fine in **3.11.0-12 (**and lo and behold, knock on wood, the wireless issue has not re-surfaced.....yet). But, it's really annoying to have to always boot by selecting Advanced Options. 

I would remove the more current (albeit non-functional) kernel via the Synaptic Package Manager...but the manager in 3.11.0-12 doesn't see its more "advanced" counterpart. And I can't boot into the newer version to remove it from there (if I even could while it's the "active" kernel).  


Can I boot into a Live CD and manually delete all the **3.12** boot files, then safely reboot back into **3.11** to run a GRUB update? Or will doing this mess me up on boot? How can I safely get rid of the **3.12** kernel? 

Also, has anyone else experienced issues with wireless connectivity with Ubuntu, and if so, what did you do to solve it permanently? 

Thank you in advance. Cheers. :-)


EDIT: The post title should read "updated" kernel, not "updating."

---

### Post by Avatas on 2014-01-26
[COLOR=#000000]mknudsen84-e,
[/COLOR]I use the same USB NIC (Linksys AE1000) as you and I have also been experiencing the same connectivity issues. I get a string of: 

**[40828.299957] ieee80211 phy0: rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x101c with error -71**

in dmesg and I've found my only recourse is to unplug the device. 

I am running 3.11.0-15-generic. At least you fixed the nic problem, wish I could help with your other problem. bump+1

---

### Post by mknudsen84-e on 2014-02-12
Thank you Avatas. I appreciate the reply. :-)

---

### Post by strungoutfan78 on 2014-02-19
Hey mknudsen84-e.  My name is Neil and I'm in your CIS291 class.  I posted a reply in the discussion board but I wasn't sure if you saw it so I'll post it here as well:

I see it looks like you solved the wireless issue, correct?

As far as setting the default boot option, you need to peroperly configure GRUB so it knows which one you want.  Take a look at this quick tutorial here:
[http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/](http://linuxnorth.wordpress.com/2011/03/09/grub2-revisited/)

There is also a link in the tutorial to a very detailed breakdown of exactly how GRUB2 works and what it is you're tinkering with.
You can find it here:[http://www.dedoimedo.com/computers/grub-2.html](http://www.dedoimedo.com/computers/grub-2.html).

The direct link to the section you probably are interested in is:
[http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480](http://www.dedoimedo.com/computers/grub-2.html#mozTocId624480)

****DISCLAIMER****
I'm using Debian Stable which is a bit behind Ubuntu as far as versioning, but I'm fairly certain this info is pretty much standard for
most current Linux distributions.  Double check before you take my word for it.

The file you'll be interested in is /etc/default/grub.  There's a line that reads: GRUB_DEFAULT=0 (or something similar).
Next time you boot pay attention to the menu and note the position number (starting with zero for the top entry, then 1 & so-on).
Then you'll change the number following GRUB_DEFAULT= to whatever number the line that contains your kernel of choice corresponds to.
Another option mentioned in this tutorial is instead of using an absolute value for your default boot selection you may enter
GRUB_DEFAULT=saved, which will boot the same choice used on your previous boot.

Not sure why everything got so ridculously complex moving from legacy GRUB to GRUB2.
It would be nice if we could still just edit the menu.lst file and be done with it.
I hope I understood the question correctly and that this helps.

---

