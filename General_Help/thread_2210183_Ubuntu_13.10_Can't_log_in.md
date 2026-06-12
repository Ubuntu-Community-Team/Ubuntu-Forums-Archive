---
title: "Ubuntu 13.10: Can't log in"
date: 2014-03-09
forum: General Help
---

### Post by Nelson_Batista on 2014-03-09
So I've tried just about every fix I could find out there, but I still can't log in to my account. When I enter the correct password, the screen goes black for about a second, the cursor disappears, and after another second it brings me right back to the login screen. I can log in to the guest account without any issues, but not the one I normally use. For reference, I've tried all these possible solutions:

sudo mv ~/.Xauthority ~/.Xauthority.backup
Nothing happens. Exact same issue.

sudo apt-get remove --purge cinnamon*
sudo apt-get autoremove
Tells me cinnamon is not installed. Issue continues.

ls -lah
chown "username:username" .Xauthority
"username" = my username. No errors, but the issue persists.

ls -ld /tmp
sudo chmod a+wt /tmp
Still no errors, but no sign of being able to log in.

sudo dpkg-reconfigure lightdm
Works in the background for about a second and.... nothing. Issue persists.

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates
sudo apt-get update
sudo apt0get install nvidia-current
Update of Nvidia drivers proceeds with no errors, but it does nothing to correct my issue.

sudo service lightdm restart
Kicks me back to the login screen but the issue persists.

sudo rm ~/.Xauthority
sudo rm ~/.Xauthority
Nothing happens.

Reinstall Ubuntu (twice.)
Nothing changed either time.

sudo rm /etc/X11/xorg.conf
sudo rm/etc/X11/xorg.conf.failsafe
Nothing happens.

Anyone have some Ideas?

---

### Post by Bashing-om on 2014-03-11
Nelson_Batista; Hi !

Maybe a problem with "XAUTHORITY" ?
This thread refers:
[http://ubuntuforums.org/showthread.php?t=2151518](http://ubuntuforums.org/showthread.php?t=2151518)

All else I can thing of, seems you have done all other checks.

[INDENT][INDENT]where there are solutions there are no problems
[/INDENT][/INDENT]

---

### Post by newbie2244 on 2014-03-11
Greetings-

Do you by any chance have a dual booting system? if so, you could rename Ubuntu folder (root.disk), re-install Ubuntu and then mount the renamed(original) root.disk to get any data off it. I did just what you did a while back. But since I had a dual boot system I was able to do a wor-around. 

Good luck. 

Regards

---

