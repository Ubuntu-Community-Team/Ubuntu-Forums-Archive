---
title: "More problems w/Ubuntu"
date: 2008-02-11
forum: General Help
---

### Post by VinceW on 2008-02-11
The dual monitor problem in previous post is only an inconvenience, my printer not working is a real problem. I am running a Sony Vaio laptop model PCG-K47.
The Epson CX9400 all in one is listed in the setup/config utility but will not run.
I would have thought by now these sorts of problems would have been worked out.
It's no wonder so many people are using MS and Apple.

---

### Post by danwood76 on 2008-02-11
try using the driver for the 'Stylus CX5000F' they are very similar printers and I have read they are compatible at printing at least.
You will have to wait for the drivers to update in the repositories to get the full driver working.

The problem you have with this printer is that it is fairly new and epsom dont write linux drivers so you are stuck with waiting.
Go complain to epsom!

---

### Post by packetman on 2008-04-21
Ok, lets carry this a bit farther down the road.

I seem to have gotten myself in an interesting pickle with this printer.  It is attached to my home network as a windows printer via a Windows XP system.  I can see the printer on the network no problem.  I ran into the whole driver issue and went searching for a driver.  On sourceforge I found the source code for the CX9400FAX (the version we are running) and downloaded it.  I did the .configure, make, and make install. In 5 years of compiling source into executables this had to be the FIRST time all three steps went off without a hitch.

That should have been my first tip off, because after this, not only could I not print to this printer on the network, I also could not print to the Epson Stylus Photo R200 I have connected on a USB port.

uh oh.

Ok, so I figure lets uninstall gutenprint and foomatic, reinstall and try again.  After several iterations of this, now I get "The CUPS server cannot be contacted" when tryning to define printers.

Ok, so have I over thought this problem?

I have some questions about why the windows server piece isn't working on this system too, but that is another forum post an not nearly as important to me.

Thanks, Craig

---

