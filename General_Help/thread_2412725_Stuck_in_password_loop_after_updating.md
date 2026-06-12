---
title: "Stuck in password loop after updating"
date: 2019-02-16
forum: General Help
---

### Post by KieranFitzgerald on 2019-02-16
Ubuntu 14.04 64 bit.
Updated yesterday and I am unable to log in. The system is stuck in a loop asking for my password.  I have searched for similar problems on the forum but most are related to other versions.  I can start a terminal and I have checked authorities, these appear to be correct.  Help in getting the system working would be appreciated.  Thanks

---

### Post by dragonfly41 on 2019-02-16
You need to search "Ubuntu 14.04 NEAR Xauthority" ..

[https://ubuntuforums.org/showthread.php?t=2310257](https://ubuntuforums.org/showthread.php?t=2310257)

Using LiveUSB you can access the Xauthority file and change permissions.

Here is a [blog (12.04)]("https://idiallo.com/blog/ubuntu-infinite-login-loop") explaining how to access Xauthority.

---

### Post by KieranFitzgerald on 2019-02-16
The permissions are correct as far as I can tell.  Updating NVIDIA drivers did not help.  When installing the NVIDIA stuff I was asked for a secure boot password.  I was also asked for this during the update which broke the login.  My system is set for insecure boot.  I'm sure this was to fix a similar log in problem some time ago.  So frustrating.

---

### Post by dragonfly41 on 2019-02-16
I can only suggest .. keep searching for clues .. don't give up .. you will learn a lot .. 

[https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop)

---

### Post by CatKiller on 2019-02-16
> **KieranFitzgerald said:**
> Ubuntu 14.04 64 bit.
Updated yesterday and I am unable to log in. The system is stuck in a loop asking for my password.  I have searched for similar problems on the forum but most are related to other versions.  I can start a terminal and I have checked authorities, these appear to be correct.  Help in getting the system working would be appreciated.  Thanks

That sounds exactly like a graphics driver problem: you aren't being logged out, X is crashing and the first thing that happens when X restarts is that you get the login screen.

---

### Post by KieranFitzgerald on 2019-02-16
Ok logged in.  
Used this from [https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop](https://askubuntu.com/questions/223501/ubuntu-gets-stuck-in-a-login-loop) thanks dragonfly41

sudo apt-get update
sudo apt-get -y dist-upgrade
sudo apt-get -y install fglrx
Think this replaces the graphics driver.  When rebooting I enabled secure UEFI boot.
Bingo off we go.

Don't ask me how, about log out and back in to check.

---

### Post by KieranFitzgerald on 2019-02-16
All working.
Must upgrade should I go via 16.04 to 18.04

---

### Post by deadflowr on 2019-02-16
installing the fglrx driver is a short term solution since that can only run on 14.04.1 and 14.04 is heading toward end of life in April.
Can you upgrade or try a newer release?
There are probably a load of things better in newer releases.

Edit: 
I see the next post that came as I wrote this post:
> Must upgrade should I go via 16.04 to 18.04 
Try 18.04 from a fresh install.

---

### Post by CatKiller on 2019-02-16
If you're upgrading, you'd need to go through 16.04 first. There's no tested upgrade path from 14.04 to 18.04.

Many people would recommend doing a fresh install rather than an upgrade.

---

### Post by KieranFitzgerald on 2019-02-18
After getting the system going Windows no longer booted so I did a boot repair from a live USB.  This has completely destroyed the boot setup.  The original menu had 4 or 5 entries.  The "repaired" menu has 10 entries 3 for Windows the rest are Ubuntu with the top entry starting an old installation.  When I ran boot repair it turned off secure boot.  Windows now boots.  Please what do I do now?

Edit my main Ubuntu boots from the boot menu entry for the old install!

Starting a new thread for this.

---

