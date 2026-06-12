---
title: "Synergy Autostart"
date: 2005-08-20
forum: General Help
---

### Post by darksbane on 2005-08-20
Hey hey, I'm new to the forums as you can probably see but I've been playing around with Ubuntu for a day or two now and have had some experience with other distros before. Anyways, I've installed Synergy through Synapse and it seems to be working perfectly. The problem I'm having is in getting it to run at the startup. I've followed the instructions here: [http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

I'm pretty sure I've found the files that it's talking about in these directories:

For the first file go to:

/etc/gdm/init/

For the second file you have to go to:

/etc/gdm/postlogin/

And for the third one I'm not 100% sure but I think its either

/etc/gdm/postsession/

or

/etc/gdm/presession/

If someone could confirm which of the last two it is that would be great :)

The main problem I'm having though is that I can't edit the files due to not being logged in as root. But the thing is, I never set a root password when I installed Ubuntu, it never asked me to, so how do I login as root to edit these files?

Any help is greatly appreciated, thanks ^_^

---

### Post by airtonix on 2006-05-05
Its not obvious, but when you created your user account, you also designated the password for your root account....but there is no root account, except through the use of the sudo command.....it allows you to run commands in the user space of root. 

sudo apt-get install leafpad

---

### Post by nwgray on 2006-05-23
[QUOTE=darksbane]Hey hey, I'm new to the forums as you can probably see but I've been playing around with Ubuntu for a day or two now and have had some experience with other distros before. Anyways, I've installed Synergy through Synapse and it seems to be working perfectly. The problem I'm having is in getting it to run at the startup. I've followed the instructions here: [http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)

I'm pretty sure I've found the files that it's talking about in these directories:

For the first file go to:

/etc/gdm/init/

For the second file you have to go to:

/etc/gdm/postlogin/

And for the third one I'm not 100% sure but I think its either

/etc/gdm/postsession/

or

/etc/gdm/presession/

If someone could confirm which of the last two it is that would be great :)

The main problem I'm having though is that I can't edit the files due to not being logged in as root. But the thing is, I never set a root password when I installed Ubuntu, it never asked me to, so how do I login as root to edit these files?

Any help is greatly appreciated, thanks ^_^[/QUOTE]

I made the change to Presession as well as Init and PostLogin. Rebooted and it works like a champ. 

Thx for the pointers on the file locations.

---

