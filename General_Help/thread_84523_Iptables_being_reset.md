---
title: "Iptables being reset?"
date: 2005-10-31
forum: General Help
---

### Post by H4rm0ny on 2005-10-31
Hi,

I've just upgraded to Breezy. I'm having a problem with the rules that I've added to iptables. Actually, the rules work fine, but I can't hold on to them. Either they're not being stored between reboots or something is overwriting them with defaults when I start up. 

I'm not an expert on this so it could be something obvious. I use iptables-save after configuring and testing the rules I've added. Are there any likely candidates in Breezy for messing up my settings. I don't have much more than the default set-up, barring some graphics programs and Knetfilter. Re-adding my rules each time is getting very annoying.

Many thanks. 

-H.

---

### Post by xlulux on 2005-11-04
bump, i need the awnser to this as well :-D for my server

---

### Post by Kyral on 2005-11-04
You should be able to make a bootup script that restores them from a file, but sadly I don't know how to do this. C'mon I'd love to see this answer too!

But to speed up the process of restoring them...

(While you have it up)

```
sudo iptables-save > file 
```

Where file is anything. I prefer to keep it in my homedir and hidden

Then to restore

```
sudo iptables-restore < file
```

---

### Post by xlulux on 2005-11-04
I read of that meathod, and im currently using it i guess i just wont shut down my computer very much anyways :-D. thanks anyways

---

### Post by xlulux on 2005-11-04
I read of that meathod, and im currently using it i guess i just wont shut down my computer very much anyways :-D. thanks anyways

---

### Post by ubuntu_demon on 2005-11-05
create a script in /etc/init.d 

sudo pico /etc/init.d/iprestore

```

#!/bin/sh
sudo iptables-restore < file

```

sudo chmod +x /etc/init.d/iprestore

sudo ln -s /etc/init.d/test  /etc/rc2.d/S15test
(this only creates the start in runlevel 2 with priority 15)

see also here :
[http://www.ubuntuforums.org/showthread.php?t=86453](http://www.ubuntuforums.org/showthread.php?t=86453)

---

### Post by H4rm0ny on 2005-11-12
**EDIT:** Ignore this last post - I'm going to find a good website on Iptables and sit down and read the lot of it. This is too important to make newbie errors. 

Many thanks for your help, people. I'm now restoring it from a file on boot-up.

-H.

---

### Post by ubuntu_demon on 2005-11-12
np :)

(I have create a slick traffic shaper that starts at boot-up. But it isn't (yet?) very user friendly.)

---

### Post by Shadow_Knight on 2006-08-05
I am not sure this will help out or not, but it helped out with Ubuntu 6.06 and my iptalbes resetting.  The following link provides a good explanation as to what the problem is and how to go about fixing it.

[http://www.ubuntuforums.org/archive/index.php/t-19106.html](http://www.ubuntuforums.org/archive/index.php/t-19106.html)

I am hoping you can adapt the script to Kubuntu 5.10 as well as the commands.  If you can not, I apologize since I am still new to linux as well as learning how all the various versions of Ubuntu are related.

---

