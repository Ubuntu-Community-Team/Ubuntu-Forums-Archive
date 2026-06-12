---
title: "X crashed"
date: 2007-06-18
forum: General Help
---

### Post by embeemb on 2007-06-18
I just upgraded to Edgy. Trying to install Beryl, I followed the how-to on the Beryl Wiki plus this [http://www.ossgeeks.co.uk/?p=70](http://www.ossgeeks.co.uk/?p=70) in order to get AIGLX up and running.

Upon restarting X (ctrl + alt + bkspace), X server wouldn't log on. It gives back an error that no screens are found.

 I logged in to XP and installed this ap to be able to view ext2 and ext3. I removed the edits previously made to /etc/X11/xorg.conf file, saved and closed the file. But X server still won't load.

I'm desperate here. What do I do ?

---

### Post by DagMan on 2007-06-18
Try logging in just at the command line with your username and password, or hit ctrl-alt-f1 to acheive this if you can't figure out how to boot into the other kernel.
Then try this 
```
sudo dpkg-reconfigure xserver-xorg
```
If you make it back to the gdm login screen choose to change the session, choose gnome-failsafe, and take that beryl entry out of your sessions
Hope it helps.

---

