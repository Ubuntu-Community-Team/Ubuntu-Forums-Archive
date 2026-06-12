---
title: "Using liveCD to recover files"
date: 2006-11-06
forum: General Help
---

### Post by chrisblue on 2006-11-06
update: Inital problem fixed so didn't have to back up with the live CD.

=================================================


Hi, I seem to have broken my system trying to install xgl and haven't received much advice so thinking a reinstall might be the easiest way to get back up and running.

Can anyone help me to understand how I can access my home directory  when using the livecd. If i try to log in as a different user the log on screen won't accept my user name and password.

All I want to do is back up my files to a CD or to a different partition and then reinstall (or better yet fix my screw up but I don't know how to go about doing that)

Thanks

---

### Post by taurus on 2006-11-06
you're probably just hosed your X so you just have to reconfigure it again.  Boot into recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```
Once you're done, reboot and see if X comes up now.  

Otherwise, post back and I will show you how to mount your harddrive using the LiveCD.  ;)

---

### Post by galego on 2006-11-06
taurus, 
i am actualy in the same position. except in trying to get my ATI driver updated i decided to not follow the how to and well..... then in the process of my infinate wisdom i decided to delete the mesa driver through synaptic and now i dont have gdm. all i get to is log in  at the command prompt. i can log in using "startx" but i cant use syanptic (error file missing or corrupt). when i look at my xorg.conf it is empty, when i replaced it from the backup i still get nothing just the command prompt log in. i think i really jacked it up. is there a way to repair the system? i am this close i just giving up. :-?

---

### Post by taurus on 2006-11-06
> **galego said:**
> taurus, 
i am actualy in the same position. except in trying to get my ATI driver updated i decided to not follow the how to and well..... then in the process of my infinate wisdom i decided to delete the mesa driver through synaptic and now i dont have gdm. all i get to is log in  at the command prompt. i can log in using "startx" but i cant use syanptic (error file missing or corrupt). when i look at my xorg.conf it is empty, when i replaced it from the backup i still get nothing just the command prompt log in. i think i really jacked it up. is there a way to repair the system? i am this close i just giving up. :-?
Okay, sounds like you just need to install gdm and activate it again.  After log in (dont run startx, yet), type

```
sudo aptitude update
sudo aptitude install gdm
sudo /etc/init.d/gdm start
```
Now, if you press <Alt>F7, you would see a GUI login screen.  Otherwise, reboot.

---

### Post by chrisblue on 2006-11-06
> **taurus said:**
> you're probably just hosed your X so you just have to reconfigure it again.  Boot into recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure xserver-xorg
```
Once you're done, reboot and see if X comes up now.  

Otherwise, post back and I will show you how to mount your harddrive using the LiveCD.  ;)

Tried that but I get up to where I have to set the colour depth and then the utility quits out with a warning about over writing a file and suggest backing up and continuing. I did copy the file to a back up but don't see how to continue. If I start it again it still quits at the same point. If you can help me get around that point I may be able to reconfig and fix it.

---

