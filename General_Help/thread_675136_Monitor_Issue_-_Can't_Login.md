---
title: "Monitor Issue - Can't Login"
date: 2008-01-22
forum: General Help
---

### Post by innocenceisdeath on 2008-01-22
I can no longer log on to my computer, once it reaches the login screen the display goes weird and switches to a load of text.

Due to the obscurity of my monitor I could not set it as the correct one, but somehow I had found one which I'd been using for a while. But it seemed to think the monitor was widescreen, somehow it was fine once logged on, but on the logon screen it would be a widescreen resolution. Hence I decided I would try to fix it. So I went to reconfigure my monitor and found one that seemed to work fine, it then said I needed to restart in order for the changes to take place. So I went ahead and did that.

Upon rebooting it told me that the settings were wrong, and it gave me the window to reconfigure them, so I went ahead and found another. I then noticed that the drivers were not set to fglrx for the current settings, so I changed these back again. The screen then just went black. I tried Ctrl+Alt+Backspace, but this made no difference. So I rebooted, and am now face with the problem mentioned at the start.
I tried plugging in another monitor but the made no difference.

Btw if it makes any difference my monitors art CRTs.

All help is appreciated.

---

### Post by silviur on 2008-01-22
sudo dpkg-reconfigure xserver-xorg

At the monitor screen, choose Medium or Advanced and choose or type the frequencies, if you know them. 
Anyway, the main thing is to choose Test next time at the reconfigure stage, and restart only after you found a monitor/driver which works.

---

### Post by rosegarden78 on 2008-01-22
That sure beats having to re-install from scratch if all else fails.  :KS

---

### Post by innocenceisdeath on 2008-01-22
Thanks, I will try that in a minute.

The weird thing is i *did* click test! And it worked! o_0 I checked a couple times too, cos I've had hell of a lot of problems with this old monitor. I'm looking into buying a new one, which will hopefully sort out any problems.

Thanks a lot, if all fails, I have a spare HDD I can move everything to.

EDIT:

I have now tried this and it works! Thanks! Buuuuuuut... Now it can't detect my mouse and there are loads of options for mice when reconfiguring :S May have to go through each one >.>

---

