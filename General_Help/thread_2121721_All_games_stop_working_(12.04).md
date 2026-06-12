---
title: "All games stop working (12.04)"
date: 2013-03-02
forum: General Help
---

### Post by razing32 on 2013-03-02
Hi ,

I have been running Ubuntu for a while now and was able to run games on it , wether Steam or GOG games thourgh wine they worked.
Recently , after a few updates  (nothing of consequence i think , curl , some language plugins for Mozilla), everything stopped working.
I even notice some odd desktop bugs like the icon for Dosbox showing a blueish tint.

Also if I run a game the screen either goes black or it minimizes to  a low resolution. I try Ctr+Alt+F1 , an try kill and sudo kill of the  process running the game and no luck. Process is still running.

I tried some fixes to reinstall xorg-xserver and reconfigure it. Still no luck

My grpahics card is NVIDIA GeForce GTX 570 HD .

---

### Post by razing32 on 2013-03-03
Ok , so after some tips from a friend and some struggling I fixed it.
Seems the issue is Steam's client only works with latest NVIDIA drivers.
Once i updated steam everything died gaming wise.
Once i updated the nvidia drivers everything worked.

Here's what i did.

Ctrl+Alt+F1
sudo stop lightdm (can be gdm or kdm , to stop X)
lsmod ( i identifed current nvidia driver so i can block it)
edited /etc/modprobe.d/blacklist.conf and added the driver from before to blacklist
nvidia-installer --update (note : it still get a pre-install script error but i chose to ignore it)
it updated and i let it do the backups/settings recommended
i rebooted and all was well

Hope this helps anyone who has this issue.

---

### Post by xp15 on 2013-03-03
Thanks for posting the solution too, It sure will help many others.
^^

---

