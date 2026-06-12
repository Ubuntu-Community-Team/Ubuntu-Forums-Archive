---
title: "Session locked - wait few seconds - wait for ever!"
date: 2015-08-28
forum: General Help
---

### Post by makem2 on 2015-08-28
I reinstalled ubuntu and had everything working correctly dual booting with windows after quite a struggle to get all working.

A software update notification came up and there were some 300mb of updates. I started these off and left the machine for tea.

When I returned the screen was blank and when I pressed a key I had the message "This session is locked, you will be directed to unlock procedure in a few seconds". After 20 minutes I was still stuck in that screen and was forced to reboot.

When ubuntu returned it said an internal error had occurred and if I noticed a problem to reboot. Networking was disabled. Reboot- no change.

I used grub to get to a 'repair' facility and found that now I was logged in without any /home data. I appear to be 'makem' although the fresh install after a format I chose makem2 as username.

I rebooted and the makem2 username allowed login but again I had the internal error warning, networking was disabled and probably other things missing.

I installed the updates which had been downloaded and rebooted - no change.

I have another corrupted installation.

Is there any way to 'refresh' the system to recover settings or must I reinstall once again and hope this time it works even if I leave. What about the two usernames? Is that why a session was locked?

[edit] Checking the grub entry I now have and extra user!

I have the usual 'Ubuntu' at line one and below that another ubuntu on sda9 which if I choose it is 'makem/home'

I appear to have ubuntu on sda 7 where it should be and a spurious ubuntu from a previous install on sda9

The first one has an internal error problem and the second does not have any data in /home

---

### Post by dino99 on 2015-08-28
which ubuntu is it ?
if you boot from the grub's 'recovery' mode, then you can activate the network, then open a terminal to do some checking:
> sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
sudo dpkg --configure -a

then reboot as usually, but remove 'quiet splash' from the grub line (hit 'E' to edit the grub line, then save & continue booting; that will get you see the verbose booting processes, and so to know where it hang

---

### Post by makem2 on 2015-08-29
I got in such a mess!

I finally decided I should reinstall Win 8.1 and then start again

After installing 8.1 I decided to install Win 10 first!

Now I have a fresh small Win 10 and a large fresh Ubuntu :D

---

