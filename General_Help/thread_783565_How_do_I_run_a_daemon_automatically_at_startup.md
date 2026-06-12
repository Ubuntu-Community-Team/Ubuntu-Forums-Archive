---
title: "How do I run a daemon automatically at startup?"
date: 2008-05-05
forum: General Help
---

### Post by mjpatey on 2008-05-05
Hi,

I just installed a little media sharing server called ushare, which I'd like to run as a daemon at startup (it has a daemon mode, so that part is covered).  It looks like "scheduled actions" are added using anacron or atd, according to a brief description I found under System --> Services.  But I can't find a way to start either task scheduler.

Anybody know how to have a daemon automatically start at startup?

Thanks!

-Mark

---

### Post by spudratic on 2008-05-05
pretty sure you do this in sessions or session manager.use these 2 in the search to see what you can find I have added programs at startup this way.However I  do not know enough to walk you through it.The good news is threre is a guide I find from time to time when I need to do it.I also keep forgeting to bookmark it so I don't have the link.I hope this little bit of info helps.

Edit sorry I think I read your post incorrectly please ignore if this is not what you want to do.

---

### Post by pmaconi on 2008-05-05
Open System -> Preferences -> Sessions. Click the "Add" button. The first field is whatever you want to call the scheduled session (what you type here appears as bold in the list). The second field is the most important one - whatever the command that you want to run at startup is. For example, I need to start BTNX when my computer starts to use the extra buttons on my mouse. I filled this field in with "btnx" - the terminal command to start the daemon. The third field is just a short description of whatever your task is doing. Hope this helped.

---

### Post by tim71 on 2008-05-06
Normally daemon has a initialization script in /etc/init.d/ directory.

It can be run manually if needed - for example
```
sudo /etc/init.d/pulseaudio start
```

If daemon has to be initialized in startup, then a link to this script is put into startup initialisation directory - they are /etc/rc0.d/ ... /etc/rc6.d/ (number is for runlevel: 0-shutdown, 1-single-user mode, 2-normal operation, 3...5-not used in Ubuntu, 6-reboot).

Operation is determined by a name of the link - first letter determines the action (S-start, K-kill), following number (01-99) determines the sequence of these scripts in this directory.

For example btnx has startup file '/etc/rc2.d/S49btnx', which is linked to '/etc/init.d/btnx'

If some program has to be run in userspace with rights of a current user, then it can be doen by adding the command or script in session startup.

---

### Post by mjpatey on 2008-05-06
Spudratic, I gave you a "thanks" because your post was very helpful, but a the same time hilarious!  You sound just like me... I have to revisit these things everytime they come up, and re-learn them.

Thanks to the rest of you, too... I appreciate all the info!  tim71, I might give that a shot if I can set aside the time.  Thanks!!!

-Mark

---

### Post by Oldsoldier2003 on 2008-05-06
> **mjpatey said:**
> Spudratic, I gave you a "thanks" because your post was very helpful, but a the same time hilarious!  You sound just like me... I have to revisit these things everytime they come up, and re-learn them.

Thanks to the rest of you, too... I appreciate all the info!  tim71, I might give that a shot if I can set aside the time.  Thanks!!!

-Mark

[http://ubuntujourney.wordpress.com/2008/04/18/starting-a-program-at-boot/](http://ubuntujourney.wordpress.com/2008/04/18/starting-a-program-at-boot/)

a more in depth look at it if you have the inclination to go the init script route

---

