---
title: "Problem with suspending under 13.10"
date: 2014-02-15
forum: General Help
---

### Post by WimiBuntu on 2014-02-15
Dear all 

I have a ThinkPad T430s with Ubuntu 13.10 and there is a problem with suspending. Very often (but not always) when I close the lid, the computer tries to suspend (the indicator with the moon blinks), but then returns to the battery symbol and the computer does not suspend after all.

Where should I start searching for a solution?

Best regards

---

### Post by pierhyth on 2014-02-25
Hi WimiBuntu,

I don't have an answer for you unfortunately.  But I just wanted to say that I am experiencing the same issues.  I have recently installed 13.10 on a T430s.  When I suspend, it seems to suspend briefly and then resume shortly afterwards.  I get the same thing happen, whether I close the lid, select "suspend" from the menu in the top right corner of the Unity desktop, or whether I issue a suspend from the commandline doing "pm-suspend".

I've looked in

  /var/log/pm-suspend.log

It seems to successfully suspend, and then a few seconds after, seems to do a resume:

Tue Feb 25 21:16:43 CST 2014: Running hooks for suspend.
...
Tue Feb 25 21:16:44 CST 2014: performing suspend
Tue Feb 25 21:16:47 CST 2014: Awake.
Tue Feb 25 21:16:47 CST 2014: Running hooks for resume

I have no idea what is triggering the Awake.

Cheers.

---

### Post by pierhyth on 2014-02-25
Some success!

I found this link...
[INDENT][http://askubuntu.com/questions/144932/why-does-my-laptop-resume-immediately-after-suspend](http://askubuntu.com/questions/144932/why-does-my-laptop-resume-immediately-after-suspend)[/INDENT]

which seems like it has some useful approaches.

In particular, I had a go at doing what the second response suggested.  I compared the output of "lspci | grep USB" against the output of "acpitool -w" and saw that there were three usb devices that were configured to wake.  They were XHCI, EHC1 and EHC2.  I really don't know what these are, or why they might be configured to wake.  But I used "sudo acpitool -W 5" etc to disable these three for wake.

When I did this, I can now suspend and it all seems to work fine - no resuming a few seconds after suspend anymore!

I still don't properly understand what is happening here.  And I do wonder whether there are any negative side-effects to disabling XHCI, EHC1 and EHC2.  But at least I seem to have suspend working now!

I am probably going to add this fix to /etc/rc.local along the lines of the first response.  Hopefully this will apply the fix every time I boot up ubuntu.

Another link which may be relevant is...
[INDENT][http://wiki.xbmc.org/index.php?title=HOW-TO:Enable_Wake-On-Device_for_Ubuntu](http://wiki.xbmc.org/index.php?title=HOW-TO:Enable_Wake-On-Device_for_Ubuntu)[/INDENT]

Anyway, hope this solves your problem also.

Cheers.

---

### Post by WimiBuntu on 2014-02-26
Thank you. 

A friend of mine, who has way more experience with Linux than I have, looked into the log files and he says it has something to do with the eth0 driver/port/something. I will ask him again for more specifications.

Best regards

---

### Post by WimiBuntu on 2014-02-28
Well, I asked my friend again. He told me that he could see from dmesg that the suspend mode fails due to the e1000e driver. He further told me that I can circumvent that problem by unloading the driver via rmmod e1000e.

---

