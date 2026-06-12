---
title: "Urgent: Can't get Unity GUI to work after closing LightDM! (Ubuntu 14.04)"
date: 2015-05-12
forum: General Help
---

### Post by SteveL1990 on 2015-05-12
Hi there. It's been a while since I've posted on the forums, but I've unfortunately run into a serious problem and I could really some help ASAP. 

For a little background: Earlier this morning, I couldn't help but notice that my computer was running a little slow, and, thinking I could so a soft reboot of a sort, I  decided to try to close Xorg using the System Manager(btw, I had done  this a couple of times before without any ill effects). Unfortunately,  the program wouldn't come up when I was using Unity, so I had to search  for another way to do it, through the terminal(and logging into the  root). There were a few initial commands, picked up from various AskUbuntu threads, that I tried: 

> kill xorg
kill 1
pkill
pkill -s
pkill -f
pkill xorg
pkill -s xorg
pkill xorg -f
pgrep -f '^/usr/bin/x '
pgrep -f '^/usr/bin/x '

None of these, however, really did much of anything. I did eventually find a command that worked, and that was: 'sudo /etc/init.d/lightdm stop'

Unfortunately, however, as it turned out, this was only just the beginning of my problems: when I rebooted, everything seemed to boot up normally, but then it just went to a blank screen. As in totally blank. I rebooted the PC again and decided to try to go into recovery mode-first thing I tried was to do a disk-check via the fsck utility(which helped me solve an earlier issue), and then try to boot via the Failsafe Graphics option: that didn't work, not even after a couple more tries. I eventually realized that I could at least load the basic root system by pressing Ctrl+Alt+F1, so, with that, I decided to keep looking for potential solutions.

After dropping back to the root, I immediately tried reloading LightDM via 'sudo /etc/init.d/lightdm start'.....which didn't work. I then tried 'sudo /etc/init.d/lightdm restart', which also failed to produce any meaningful results after I pressed Ctrl+Alt+F7 to try to go back to the GUI. Even the force restart option didn't work. So I kept pressing on.

sudo Xorg -configure returned a message that said:
> 
Fatal server error:
Server is already running for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again

(there were other things I tried afterwards, until this point, and I'll do the best I can to update this post so I can fill in the details ASAP!)

I honestly don't know what else to do here-Nothing I've tried has worked, and unfortunately, I apparently can't reinstall my Ubuntu system without erasing all my documents, pictures, and stuff. I am getting a little desperate right now, so any help at all would be appreciated at this point. :(

---

### Post by SteveL1990 on 2015-05-12
Okay, so, I'm not exactly sure how I managed to do this.....but I managed to get Ubuntu working again. I did go thru the Failsafe Graphics option one last time thru the Recovery Menu, and managed to load a backup graphics setting: maybe that did it? In any case, perhaps it might not hurt to leave this thread open for a while, mainly to help other people who might have gone thru the same issue I did.

---

