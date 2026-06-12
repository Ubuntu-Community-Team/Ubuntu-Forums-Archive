---
title: "Can't Shutdown"
date: 2006-08-04
forum: General Help
---

### Post by beanstalker on 2006-08-04
Hi, recently had ubuntu installed by a friend and have since installed ndiswrapper and about 150 updates, but ever since installing updates, I have not been able to shutdown properly, the only options on the shutdown menu being: Log-out, Lock-Screen, Switch User and Hibernate. I have tried logging out and then shutting down, but still no shutdown or restart option on menu. Would appreciate any help.

Thanks, Jack :confused:

---

### Post by cantormath on 2006-08-04
> **beanstalker said:**
> Hi, recently had ubuntu installed by a friend and have since installed ndiswrapper and about 150 updates, but ever since installing updates, I have not been able to shutdown properly, the only options on the shutdown menu being: Log-out, Lock-Screen, Switch User and Hibernate. I have tried logging out and then shutting down, but still no shutdown or restart option on menu. Would appreciate any help.

Thanks, Jack :confused:

An alternative to shutdown would be open the terminal and type

```
sudo shutdown
```
or
```
sudo reboot
```

But that does not fix your menu situation.  Did you "friend" just install ubuntu, or did he maybe change some of your user right, like maybe, disable your user to shutdown, possible accidently trying to keep you from making a mistake.

Try the sudo shutdown, if you are not in the admin group, you probably got taken out.  When it asks for password, type the password that you use when you login.

---

### Post by beanstalker on 2006-08-04
Thanks, have been using "sudo shutdown -h now" on advice from another thread, and that does seem to work. My friend only installed ubuntu, (he didn't actually finish that, i did the rest), and i have checked my user privilages and I can't find anything disabled (I have also used "adduser user admin" in root to give myself admin privilages).

---

### Post by beanstalker on 2006-08-04
Hi, yes that helps, thank-you, its seems to shutdown now, but I would still like to be able to add the shutdown and restart options back to the shutdown menu, if anyone has any ideas......

Thanks, Jack

---

### Post by cantormath on 2006-08-04
> **beanstalker said:**
> Thanks, have been using "sudo shutdown -h now" on advice from another thread, and that does seem to work. My friend only installed ubuntu, (he didn't actually finish that, i did the rest), and i have checked my user privilages and I can't find anything disabled (I have also used "adduser user admin" in root to give myself admin privilages).

Im happy that worked for you.

You should not be running as root, at least not most of the time, and never in login as root in gnome or kubuntu, its not needed and its not safe.
you had to create a user when you installed ubuntu.  That user should be able to shutdown and should NOT be part of the root group.

---

### Post by beanstalker on 2006-08-04
> **cantormath said:**
> Im happy that worked for you.

You should not be running as root, at least not most of the time, and never in login as root in gnome or kubuntu, its not needed and its not safe.
you had to create a user when you installed ubuntu.  That user should be able to shutdown and should NOT be part of the root group.

Thanks, interesting you mentioned that because after I installed and created a user it would not let me log in with that username and password, so I rebooted in recovery mode, reset the root password (which I didn't know) and tried to reset the password for the user I created during installation, however it told me that that user did not exist (I tried various different spellings of the username) so created a new user "adduser user" and have been using that user ever since (I had to add it to the admin group to install ndiswrapper). This user was able to shutdown and reboot and everything else until after I rebooted after installing  a whole load of updates. 

Thanks Jack

---

### Post by beanstalker on 2006-08-04
> **cantormath said:**
> Im happy that worked for you.

You should not be running as root, at least not most of the time, and never in login as root in gnome or kubuntu, its not needed and its not safe.
you had to create a user when you installed ubuntu.  That user should be able to shutdown and should NOT be part of the root group.

I will try removing my user from root group and see if it helps.
If still no luck, I might try creating a new user and removing the old one.

Thanks, Jack :confused:

---

### Post by beanstalker on 2006-08-04
> **beanstalker said:**
> I will try removing my user from root group and see if it helps.
If still no luck, I might try creating a new user and removing the old one.

Thanks, Jack :confused:


Still no luck, tried a new user but to no avail, anyone with any more ideas........

Thanks, Jack :confused:

---

### Post by Brain Juice on 2006-08-04
Is gnome-power-manager in your System -> Preferences -> Sessions - Start up Prgrams tab?

If not try adding it and restart x.

Info here [http://www.gnome.org/projects/gnome-power-manager/](http://www.gnome.org/projects/gnome-power-manager/)

---

### Post by beanstalker on 2006-08-05
> **Brain Juice said:**
> Is gnome-power-manager in your System -> Preferences -> Sessions - Start up Prgrams tab?

If not try adding it and restart x.

Info here [http://www.gnome.org/projects/gnome-power-manager/](http://www.gnome.org/projects/gnome-power-manager/)

Thanks for the tip, power-manager is there, will check out the link and see what it says.

Thanks :confused: Jack ](*,)

---

### Post by erusan on 2006-08-05
This sounds to me like a problem with your video card driver.  I, for instance, experience the same thing after "updating" my Ubuntu partition, which up until recently, involved installing the nvidia-glx package.  It works quite well as far as performance goes, but it won't let me restart, shutdown, restart X, etc.  I fixed it by simply installing the nvidia-glx-legacy package.  After that, I still have to force my PC to shutdown using the power button, but when it restarts running the new driver, it then restarts, shuts down, etc, without a hitch.

Hope that helps.

---

