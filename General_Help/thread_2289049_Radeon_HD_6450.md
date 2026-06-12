---
title: "Radeon HD 6450"
date: 2015-07-31
forum: General Help
---

### Post by anthony54 on 2015-07-31
I did search through the forums, but did not find quite this problem.  If it does exist and this is a repeat I sincerely apologize.

Using Ubuntu 15.04 64 bit, been running the non proprietary drivers for the video card (Radeon HD 6450).  Thought I would try the proprietary drivers and ran into a few problems.

After installing upon reboot, it does not boot to a desktop (kind of), it boots to a black screen and I think it's just stuck.  But then the mouse cursor shows up, but not as the normal arrow, rather it's an X.  Also I use the Ubuntu Dropbox addon, and for some reason that shows up as well.  But those are the only 2 items that show up, X cursor and the login box for Dropbox.  I did click on the Dropbox and login, and it opened up my dropbox folder and I could click inside the folder on files, but the window itself had no border.  All the time, still no desktop.

So I reboot to the root command prompt, uninstall the fglrx drivers thinking I will just deal with the open source ones.  They uninstall, I reboot but yet again no desktop.  This time not even the lone dropbox addon, nor the X mouse cursor.

Here is what else I am not sure of: I reboot yet again, this time I select the GRUB option with "upstart", and it booted fine.  This is ok for the moment (at least I am up and running), but if anyone can help me get the proprietary drivers working that would be great.  OR, if that is not possible, how do I get back to booting without having to hold the shift key and selecting the "upstart" option (as I am unsure what upstart is)?

Thanks in advance for any help provided.

---

### Post by anthony54 on 2015-08-02
Not sure what to say.  I downloaded Ubuntu again (same flavor), reinstalled from scratch, installed proprietary (amd) drivers from additional drivers, and all works fine.  Not sure if I did something bizarre without realizing or I just had a bad iso the first time.

---

