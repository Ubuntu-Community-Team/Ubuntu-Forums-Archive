---
title: "Upgraded to gutsy and now my screen isn't recognized"
date: 2008-03-20
forum: General Help
---

### Post by jpoRS on 2008-03-20
Hey,

I am sorry if this is a double post, but lynx doesn't seem to be playing with the search feature very well.

I tried to upgrade to Gutsy (from Feisty) today, and now that I've rebooted, the system won't recognize my screen.

I am not looking for a solution on how to make it recognize a screen yet, I just want to see if I can get it back to Feisty and then work my way back.

Thanks,
jim

---

### Post by MoLE on 2008-03-31
You may have moved on already, but in this scenario, it is probably least painful to force an update of your xorg.conf file.

Boot into rescue mode and type the following.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
sudo dpkg-reconfigure -phigh xserver-xorg
sudo reboot

```

With any luck, you should get to the gdm login screen.

---

### Post by jpoRS on 2008-04-01
I have moved on, sadly it took a lot more work than that looks like it would be if I had heard from you in time.  Thank you though, hopefully this will help some other poor soul.

jim

---

