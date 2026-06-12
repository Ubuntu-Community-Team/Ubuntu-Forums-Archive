---
title: "rm * help"
date: 2007-10-17
forum: General Help
---

### Post by Helbo15 on 2007-10-17
hi  I have made my biggest mistake since I was born and now I hope it is recoverable ^^; 

I was in the /etc/ directory when making this command 

sudo rm *

and I wanted to rm all files in /etc/webmin/

but I forgot that I was in /etc/ directory :( 

is it posible to recover whatever files it deleted  ?? or do I have to start all over ^^; ?

---

### Post by Druke on 2007-10-17
wow.... that stinks

your best bet is to check /root/.trash if it exists itherwise your pretty hosed I think

---

### Post by Helbo15 on 2007-10-17
as far as I can see there are no .trash file in /root/

I can allso see that I can't use sudo anymore :( cause it complains about no passwd file ^^;

---

### Post by Druke on 2007-10-17
yea I'd wait around here a bit longer and see if anyone says anything but I'd recommend getting a head start on a fresh install , or sleeping on it for gutsy tomorrow :popcorn:

---

### Post by Tomosaur on 2007-10-17
Woops!

Unless you can find some recovery software you're probably toast. The downside is that to install the software, and then recover any files it finds, you're going to need to be running as root :S

You MAY be able to use the recovery mode in your grub menu (ie, restart, choose recovery mode at boot menu), but I wouldn't try that until you're absolutely sure - you may have problems even booting your machine :S

Easiest solution, I would say, would be to back-up everything you can (stuff from your home folder) and then do a re-install. Sucks I know, but such is life. Linux is very powerful, but it assumes you know what you're doing.

In the future, one trick which you could use would be to create an alias for the rm command - which just moves stuff into a trash folder rather than deleting them. You can then set up a cron job or some other script to empty the trash when you feel like.

---

### Post by Helbo15 on 2007-10-17
damm :( and just the place I had placed my firewall :(  

is there a way to pull out the running firewall in to a config file  ?? ^^; 
cause it is what I have had the hardest to setup so far ^^;

I'll start to recover the config files I guess it will take me a few hours before I'm ready to do reinstall :(

however as a emergincy solution I made a passwd file with my user and the root user seems that I have most of my previusly rights back again ^^ still can't make sudo but it now complains about the group file and the sudooers file ^^

---

