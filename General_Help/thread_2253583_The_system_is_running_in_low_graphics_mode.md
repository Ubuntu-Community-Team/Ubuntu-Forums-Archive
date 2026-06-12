---
title: "The system is running in low graphics mode"
date: 2014-11-20
forum: General Help
---

### Post by Elronius on 2014-11-20
> At the moment I'm not able to enter the login graphic mode, because this appears: [http://s28.postimg.org/fx1tvydgd/DSC02351_2.jpg](http://s28.postimg.org/fx1tvydgd/DSC02351_2.jpg) Uh-oh.  I'm running 12.04 LTS and yesterday my computer stopped working with the same dialog. I am using NVIDIA as well but didn't touch the drivers as far as I know. However I was playing with the developer's version of GTK+3 and right before things stopped working I apt-get removed gtk+3.0 (although things didn't immediately break afterwards, this was the only unusual thing I did). Was thinking that perhaps Ubuntu required GTK to start up properly, but thanks to this stupid dialog and buggy behavior dropping back to command line (freezing and generally being uncooperative, which makes it seem like GTK might not be the only issue) I haven't been able to go into networking mode and reinstall GTK. (In fact, I can't reach console at all, it keeps saying my swap drive is busy or something. Was just coming on to post my own problem, now seeing this I'm a bit concerned this might be a bigger deal. :p   Anyone have any ideas of what might be causing this startup dialog? I can provide more info as needed.

---

### Post by QIII on 2014-11-20
Moved to it's own thread.

Please be courteous and do not hijack the threads of other users.  You are using a different release than the OP and have referred to taking different actions.  All users, yourself included, deserve specific attention to your specific issues.  Throwing different circumstances into the mix confuses things.

Thanks.

---

### Post by Elronius on 2014-11-20
> **QIII said:**
> Moved to it's own thread.

Please be courteous and do not hijack the threads of other users.  You are using a different release than the OP and have referred to taking different actions.  All users, yourself included, deserve specific attention to your specific issues.  Throwing different circumstances into the mix confuses things.

Thanks.

Sorry, only did because I thought the two problems might be related and thus have a similar fix.

Edit: this was the thread I was referencing seeming similar: [http://ubuntuforums.org/showthread.php?t=2253581](http://ubuntuforums.org/showthread.php?t=2253581)

---

### Post by Elronius on 2014-11-21
M(uch m)ore details (hopefully at least reader-friendly):

[SIZE=3]_**Normal Startup**_[/SIZE]
After GRUB the speakers pop and the monitor struggles a bit, then after about 20 sec I get said dialog. Mouse is functional but is an X cursor. I'm given the following options on continuing:
[B]
Run in low-graphics mode for just one session[/B]: Choosing this gives me a dialog that says "Stand by one minute while the display restarts" with Cancel grayed out and OK. It looks like there is a progress bar that is full, but it just hangs here. Selecting OK goes to a black screen, where it hangs until I reboot.
[B]
Reconfigure graphics[/B]: This gives me two options: Use default (generic) configuration, and Use your backed-up configuration. Both just refresh the existing dialog where they are given as options.
[B]
Troubleshoot the error:[/B] Here I'm given more options:
[LIST]
[*]_Review the xserver logfile_: This comes up with a log with most looking normal to my untrained eye except
[/LIST]


[LIST=1]
[*=2]/usr/share/fronts/X11/ font entries not existing (Entry deleted from font path).
[*=2]Under NVIDIA: Failed to Load module nouveau/nv/vesa/fbdev (module does not exist, 0)
[*=2]Failed to load module "nvidia" (already loaded, -1217074149)
[/LIST]

[LIST]
[*]_Review the startup errors_: I can select this but it comes up as a blank dialog.


[*]_Edit configuration file_: Selecting this just reloads the existing dialog where it is given as an option.
[*]_Archive configuration and logs_: Selecting this seems to work normally.
[/LIST]
[B]
Exit to console login:[/B] Selecting this causes the screen to go a black screen where it hangs until I reboot. **_[SIZE=3][/SIZE]_**

I've been playing with rebooting in recovery mode, and while I can get to the root prompt, I can't get networking mode to work. Also, worryingly, while fiddling about there I ran clean up obsolete files in apt-get from recovery mode and it seemed to kill off some programs I associate with Ubuntu and Unity (like unity-lens-video, as an example).

---

### Post by Elronius on 2014-11-22
Fixed. Thanks for all the help.

For anyone having the same problem, see [http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error](http://askubuntu.com/questions/141606/how-to-fix-the-system-is-running-in-low-graphics-mode-error) (and just askubuntu in general, seems a great resource that I didn't know of before this post). I was able to get networking up using a netbook's wifi connection and connecting it to my PC via Ethernet. Used apt-get to reinstall GTK, ubuntu-desktop (which seemed to reverse those worrying deletions of important things), and reinstalled the NVIDIA drivers I had. The most helpful advice in that thread for me was the bit about greping dpkg output - I found an old NVIDIA module installed (like 174) that I removed and everything started working thereafter. (Until then the dialog went away but I was booting to a black screen). 

Anyway hope this helps someone. Bye! ):P

---

