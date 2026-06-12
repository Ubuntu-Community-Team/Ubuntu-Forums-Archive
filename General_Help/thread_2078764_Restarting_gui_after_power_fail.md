---
title: "Restarting gui after power fail"
date: 2012-10-31
forum: General Help
---

### Post by Strelz on 2012-10-31
I have two ubuntu computers both running 12.04 LTS.  The first, which I will call old is running 32 bits, and the 2nd, the new one, is running 64 bits. 

The problem is power up restart.  The old one reboots back up completely when power is restored which is what I want.  The new one boots up to a TTY screen and I have to type sudo service lightdm restart to get the gui going.  This works, but I would like to have it come back like the old one.

I have been looking in all the places I can think of and I don't see any differences between the two.  The Grub files are the same for both.  

The x11 files appear to be the same also.  For example the content of 
/etc/x11/default-display-manager is /usr/sbin/lightdm  for both.

The new computer is a System76 Ratel with Intel i-7 quadcore and Ivybridge with Intel HD 4000 graphics.

I never modified any start up files on either computer.

What can I do so my new computer starts up like my old and goes right to the desktop?

---

### Post by kanikilu on 2012-10-31
If it's the same thing that happened to me, I think it's a bug in lightdm. I ran into this issue yesterday after upgrading from 12.04 to 12.10. Upon reboot, I would get a warning about it going into low graphics mode, but nothing I clicked would do anything, it would just hang, and I would have to go to another virtual console, and do what you are doing (sudo service lightdm restart).

At the moment I can't seem to find the thread or bug report where I got this information, but the hack/workaround that seems to be working for me is to add "sleep 5" above the "exec lightdm" line in /etc/init/lightdm.conf. I think they actually suggested "sleep 2", but I upped it to 5, just to be sure it waited long enough.

Other people reported that simply replacing lightdm with gdm works too...

---

### Post by Strelz on 2012-11-02
My problem is not on reboot.  It is only on power fail.  I wonder if there is some kind of power fail routine in the bios that brings it back up in some kind of 'safe' mode.  

If Ubuntu is going to replace windows which is my fond hope, we need to fix this.

---

### Post by dolphin194 on 2012-11-02
This should probably be moved to the System76 support forum.

---

### Post by Strelz on 2012-11-14
By talking to System76 I found the answer for my particular situation.  Open the System76 driver and update it.  That fixed it for me.

However, the situation as I now understand it is not really a System76 problem.  I learned that my problem is due to having a solid state drive and a very fast cpu.  So it boots up faster than some part of the boot loader is counting on and this causes some kind of gui crash on cold boot.

Somewhere in the boot loader I'm guessing there is a loop of code that is doing some kind of timing.  So I suspect this is a bug in the boot loader that only Ubuntu folks can fix.

I am anxious to see this fixed so I can continue my campaign among friends and relatives to get them off of windows and on to Ubuntu.  For the uninitiated, this kind of start up bug would have left them in dismay.

---

