---
title: "Ubuntu 12.04 fails to boot into graphical environment"
date: 2013-09-21
forum: General Help
---

### Post by Steve_Watford on 2013-09-21
Hi All,
I have an Asus laptop, running 12.04 since it was out, that now fails to boot properly into Gnome graphical environment. This occurred a month or two ago and I have been using a workaround until we were back to good enough internet to try to troubleshoot it. This is a dual boot system, but has been for years and that works ok. I can boot into windows if needed.  The boot up sequence is as follows: turn on laptop, get Asus splash then the dual boot selection menu. Select ubuntu and boot begins. I can see it starting and stopping many processes as it goes along normally. At the end is shows starting and stopping Mount network filesystems, a 15 or so second pause and then Stopping boot sequence audit. Then it just hangs. I've left it an hour at this point and nothing happens. I am on tty07 and hung. My work around is as follows. I ctrl alt F1 to get to tty01. Then enter my username, password. Then at the commandline enter sudo lightdm, then sudo password. The graphical environment starts at this point. A few second later my graphical desktop comes up and and once again I have to enter my password. The graphical environment from this point forward seems to work normally. Shutdown from Gnome appears normal all the way to power down.

Obviously, I've found a workaround, but having to login 3 times everytime you start the machine is very inconvenient. Not sure how intact the security is either at this point

Any suggestions as to what to look at or what to do? Any help would be greatly appreciated.

---

### Post by grahammechanical on 2013-09-21
I do not know if this will help at all. At the Grub boot menu select Recovery Mode. There are options at the Recovery menu that might help.

dpgk will repair broken packages
fsck will check all file systems and try to fix things

You could also try Network. That will set up a connection to the router and give Internet access but it also will put the file system into Read/Write mode. Is there a problem with mounting the partitions? Or is the problem with the lightdm display manager that runs the log in screen? May be you could re-install lightdm. Well, if you have to enter your password then the system must be secure up to the point that you get to the desktop.

Regards.

---

### Post by Steve_Watford on 2013-09-21
I had tried those on the grub repair menu before. I don't think it is at this level. It is almost like it never calls lightdm. I'm reading a bug report on a very similar/same problem right now. I tried the simple fix in there but it doesn't work for me. I guess I missed the transition to the upstart system instead of the runlevels previously used. I'm trying to find where the different upstart programs are called from and how. I see where the config files are for them, but haven't found what and how they are called now. ie, the old rc5.d directories with the S## and K## files. Interesting these are all still in the system, but from what I read they aren't used anymore. Just to confuse me I guess.  

Thanks again and if you think of anything else, please chime in.

---

### Post by Steve_Watford on 2013-09-21
I had tried those on the grub repair menu before. I don't think it is at this level. It is almost like it never calls lightdm. I'm reading a bug report on a very similar/same problem right now. I tried the simple fix in there but it doesn't work for me. I guess I missed the transition to the upstart system instead of the runlevels previously used. I'm trying to find where the different upstart programs are called from and how. I see where the config files are for them, but haven't found what and how they are called now. ie, the old rc5.d directories with the S## and K## files. Interesting these are all still in the system, but from what I read they aren't used anymore. Just to confuse me I guess.  

Thanks again and if you think of anything else, please chime in.

---

### Post by sudodus on 2013-09-21
Your work-around will be more convenient, if you enable log in directly (without the password). Then the only time you need to type the password is for sudo. The security should be OK, if your computer is fairly safe (for example in your home).

But I don't know why the graphics screen won't start automatically, yet starts nicely from your manual command.

---

### Post by Steve_Watford on 2013-09-22
Yes,  but I travel a lot and always worry about the laptop being stolen, so that isn't an option for me. 

After more reading, I would like to know how upstart works better. I see all the upstart commands in /etc/init/. Is there somewhere these are called/executed similar to the /etc/rc5.d system we used to use. Obviously, every script in init directory isn't being called.  On my system it is like the graphical environment is never called. I see no errors in syslog, dmesg or any of the other major log files. When I go to /etc/rc2.d and look at the scripts there most of them say that they have been converted to upstart commands and to use that system. What I haven't found is what/where are they actually called from?  Any help on the upstart system would be appreciated.

Thanks

---

### Post by Steve_Watford on 2013-09-23
Ok, no takers I guess. 
I can change the display manager to GDM and it works, but when going back to lightdm it behaves as described in the first post. I've been reading about upstart and think it is something there. Not sure if anyone can give me a clue???  Is this the correct forum for these questions. I am a long time linux user. Originally, RH 6.1, then years ago migrated to Ubuntu, but I'm coming up empty here. Appreciate any help/suggestions.

Thanks

---

### Post by Steve_Watford on 2013-09-23
If anyone is interested, here is the solution. Not sure why there haven't been  a lot of complaints, but hey maybe it's just me. Seems like maybe lightdm got ahead of plymouth and is calling for something in a future version of plymouth not here yet.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1188131](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1188131)

---

### Post by sudodus on 2013-09-23
> **Steve_Watford said:**
> If anyone is interested, here is the solution. Not sure why there haven't been  a lot of complaints, but hey maybe it's just me. Seems like maybe lightdm got ahead of plymouth and is calling for something in a future version of plymouth not here yet.

[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1188131](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/1188131)

I'm glad you solved the problem (or found a work-around). I have read your posts, but I had no clue what to suggest.

Did you add 'affects me too' to that bug report? If not, please do! And it probably also helps, if you describe your particular case in a new post (in that bug report). The developers read Launchpad bug reports, but they seldom care about the Ubuntu Forums ;-)

---

### Post by mastablasta on 2013-09-24
> **Steve_Watford said:**
> Yes, but I travel a lot and always worry about the laptop being stolen, so that isn't an option for me. 



ah but then you would need to have BIOS boot password set up and also disk encryption or at least data encryption (e.g. with truecrypt).

---

