---
title: "monitor not detected"
date: 2005-03-25
forum: General Help
---

### Post by bailout on 2005-03-25
I have just installed kubuntu and my monitor hasn't been detected properly. I have tried ubuntu as well by the way and no differrence.

My monitor is a Hansol 900p (19in crt) and is about 3-4 years old. The only screen about monitors that came up during install asked about deselecting possible resolutions. The main problem I now have is refresh rate limited to 60hz.

I have searched the forums and other sources and found the sudo script for reconfiguring xorg but predictably it gave the same result as during install.

Hence is my best option to edit the xorg.conf manually with my monitor specs? I think my monitor had linux specs with the win drivers for adding to x86config so do I just edit the xorg.conf to these values?

Also is there somewhere I should report ubuntu's failure to id the monitor during install so that it can be added in future? I assume that with ubuntu's reputatio for being good at detecting hardware they are keen to hear of when it fails? The monitor is relatively new and was picked up my mdk 10 which was the last linux distro I tried.

thanks

---

### Post by alastair on 2005-03-25
Look at your /etc/X11/xorg.conf file - perhaps post the "Monitor" section.

See "man xorg.conf" - you /can/ add :

HorizSync
VertRefresh

settings. But be careful (and make a copy of the file before changing).

From : [http://www.anyweb.co.uk/computers/listings/220.html](http://www.anyweb.co.uk/computers/listings/220.html)

You might have :

Scanning Frequency Horizontal 30-96KHz
Vertical 47-150Hz

---

### Post by alastair on 2005-03-25
Note also - before doing a "sudo dpkg-reconfigure xserver-xorg", it might be worth moving (renaming) the xorg.conf file - so you know a new one is created.

I'd try this again first.

---

### Post by bailout on 2005-03-27
Thanks alastair

Bit worried about getting the settings right so that it isn't able to try refresh rates that are too high. I suppose that as I only use 1024x768 and not the higher resolutions this isn't really a problem, I can simply block those resolutions.

Also surprised that a relatively new and plug and play capable monitor wasn't id'ed better by ubuntu (mdk 10 picked it up). No one has posted anything re reporting this. Ubuntu seems to have a good reputation for installing hardware but it needs to know where it fails to fill these gaps. At least some sort of database of components that don't work and how to fix them could be useful to those trying to do it manually.

---

