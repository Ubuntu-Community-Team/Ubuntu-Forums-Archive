---
title: "slow mouse scroll speed"
date: 2007-01-05
forum: General Help
---

### Post by compwiz18 on 2007-01-05
My mouse (Microsoft Laser Mouse 5000) has decided it would be fun to scroll 10 lines at a time - which is a little more then I would like.  The weird part is, yesterday it was scrolling 3 lines at a time, which was fine - my preferred speed.  Is there any way to go back to what it was doing yesterday?

When I first got this mouse, I set it up in /etc/X11/xorg.conf, and it did the same thing - scrolled 10 lines at a time.  I then removed the entry for the mouse from xorg.conf and it went back to 3 lines, however there is no entry in xorg.conf now, and it is still fast.

Thanks in advance.

---

### Post by compwiz18 on 2007-01-05
Using xev I've noticed that it the mouse emits multiple down events for one scroll, so that is the problem - I just don't know how to fix it...

---

### Post by goldgin on 2007-02-09
[http://ubuntuforums.org/showthread.php?t=336579](http://ubuntuforums.org/showthread.php?t=336579)

---

### Post by Tuxtur on 2007-06-24
A  little late I know, but this might help someone searching mouse scroll issues. I've noticed through experience that my Microsoft 5000 laser mouse will go scroll crazy after running a Windows XP session. If I reboot after a Windows XP session the mouse scroll doesn't work properly, scrolls 20 lines at a time etc. But if after using Windows XP I shutdown (powerdown) the PC and do a hard boot to Ubuntu the mouse returns to normal 

Can't explain why it acts this way, just my experience.

---

### Post by compwiz18 on 2007-06-24
> **Tuxtur said:**
> A  little late I know, but this might help someone searching mouse scroll issues. I've noticed through experience that my Microsoft 5000 laser mouse will go scroll crazy after running a Windows XP session. If I reboot after a Windows XP session the mouse scroll doesn't work properly, scrolls 20 lines at a time etc. But if after using Windows XP I shutdown (powerdown) the PC and do a hard boot to Ubuntu the mouse returns to normal 

Can't explain why it acts this way, just my experience.

Mine does that too.  I have it plugged into a USB hub that is always powered on, and it will only return to normal if I unplug it and replug it.

---

