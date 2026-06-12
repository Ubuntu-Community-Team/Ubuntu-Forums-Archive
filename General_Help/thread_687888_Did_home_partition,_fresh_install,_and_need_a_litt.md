---
title: "Did /home partition, fresh install, and need a little hand-holding with fstab"
date: 2008-02-04
forum: General Help
---

### Post by Michl on 2008-02-04
Followed psychocats to create a /home partition on a laptop,
 then did a fresh install of Gutsy, and now I have a fresh new
 /home in the /root and also the /home partition mounted as media.  So I am
ready to edit fstab as prescribed so that Gutsy will use
the /home partition as /home.  
Question 1:
I found two recommendations for editing fstab

one has
/dev/...    /home ext3   nodev,nosuid   0 2
the other has:
/dev/...   /home   ext3   defaults   0  2  

Which should I do?  The second was would require fewer changes  -- just
/media/sda4 to /home

Second question

Once I edit fstab and before I reboot, what do I  do with the fresh /home
directory in root that the fresh install just created?

---

### Post by logos34 on 2008-02-04
You did it wrong.

Reinstall, but this time in addition to the / and /swap, specify sda4 to mount at '/home', but DO NOT check the 'format' box.  This will tell ubuntu to use the existing home on sda4, mounting in the root directory at /home.

---

### Post by pebo on 2008-02-04
Don't think you need to reinstall - first try putting this line in your /etc/fstab:```
/dev/sda4 /home ext3 defaults 0 1
```Comment out the existing lines referring to /home. Then remount the partitions with```
sudo mount -a
```HTH

---

### Post by Michl on 2008-02-05
I edited fstab per instructions and mounted sda4.  My old wallpaper came back,etc.
sda4 was still mounted on the desktop, so I rebooted and everything came back
very nicely.  The only little fly in the ointment was that it took a very long time to get to
the log-in screen.  So in the search for perfection I am reinstalling since I have 
nothing to lose on this laptop.  Will follow the other method there and will see if
that makes a difference.

Thanks for the help!!

---

### Post by Michl on 2008-02-05
> **pebo said:**
> Don't think you need to reinstall - first try putting this line in your /etc/fstab:```
/dev/sda4 /home ext3 defaults 0 1
```Comment out the existing lines referring to /home. Then remount the partitions with```
sudo mount -a
```HTH

So here is my saga.  Maybe there's a lesson here somewhere.

The above edit worked fine, but boot-up was very slow, which wan't the case before in
Gutsy.  So I tried to fresh install again, but this time the install definitely froze.  So I
thought all the partitioning was a waste of time and turned-off the power and fired-up
again.  BUT lo and behold, grub was there and I booted into Gutsy, everything was
there including the slow boot.  Checked on this here in the forum and found a fix
for it -- the live cd installs the wrong resolutions for usplash.conf.  The reason I
didn't have the problem before the install was that I was running Gutsy that I
upgraded from Feisty.  So rebooted, and all is fine.

Might just add that the /home partition does not preserve all settings.  For instance,
Evolution must be reconfigured.

---

### Post by Nythain on 2008-02-05
yeah, a lot of software configurations are contained in /etc ... before i do any major reformats, reinstalls, or upgrades, i made sure to back up any important .conf or .rc files in /etc and in /home/user... makes life much easier

/home generally just saves user configurations... like user specific rc's for things, desktop appearances, themes and whatnot...

---

