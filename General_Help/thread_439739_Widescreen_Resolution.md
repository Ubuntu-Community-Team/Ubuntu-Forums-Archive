---
title: "Widescreen Resolution"
date: 2007-05-11
forum: General Help
---

### Post by efflux on 2007-05-11
Ubuntu 7.04 will not work with my widescreen at correct resolution. I have a 24 inch Eizo with resolution of 1920 x 1200 and a Radeon 9200SE card. Ubuntu 6.10 did work. I have tried to configure the xorg to the same as before but it's no go. I have the old xorg file but the configuration won't work on 7.04. I have two 3 GHz PCs sat here doing nothing for several years while I use my Mac which has not ever even had a minor glitch in two years. Windows is dire. I don't want to touch it again but Linux is worse. This is the reality Folks. Linux still remains only potentially good with all these hardware problems. This is a sad state of affairs given the new joke of an os offering from Microsoft. Maybe somebody can make a suggestion as to how I can get this working because I would really like to use these systems since a lot of software I use is actually Linux based but running on OSX.

---

### Post by Ashex on 2007-05-11
If you do a sudo dpkg-reconfigure xserver-xorg, you should be able to select the resolution during the setup (remember to leave everything as default), then save changes and restart the xserver.

I'm guessing you already tried that though. Can you paste the contents of your xorg.conf file?

---

### Post by efflux on 2007-05-11
Thanks for the reply. I had reconfigured from command as you suggested (This worked fine on 6.10 as far as I remember) and went through the xorg file as well, changing things. However I did not try simply dumping my old xorg back in. This appears to have worked. I guess the lesson here is to save all old configuration files which is ultimately what solved my problem. I'll have to study all the xorg files to see what the difference is. You can understand my frustration though. Every time I use Ubuntu something goes wrong. I had a total failure a few days ago on 6.10 with fsck death at boot. I spent ages trying to solve it then just installed 7.04 from scratch. Lets hope this will be the setup that finally works for me.

---

### Post by Ashex on 2007-05-11
Glad to be of help :)

What may have been the issue is that even though you added the resolution, the old one was set to be the primary one (this can be changed by going to system>preferences>screen resolution). 
Also, are you by chance mounting your partitions inside windows? That may have been the source of your problems (if you mount an ext3 partition as ext2 it won't use journaling, which will cause ubuntu to freak out).

---

