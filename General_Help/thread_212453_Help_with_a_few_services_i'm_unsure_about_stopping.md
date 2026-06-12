---
title: "Help with a few services i'm unsure about stopping..."
date: 2006-07-09
forum: General Help
---

### Post by shawnrgr on 2006-07-09
My palms always get a little sweaty when i start messing with the services that ubuntu has running by default. I have been following the howto "speed up... the way you can feel it" but a few services I have are not on there and a few are not describe well enough for me to mack a logical choice on stopping it or not. the following are services im unsure of.. someone please enlighten me...

loopback
mtab
pcmcia (how do I know if i have and/or use pcm cards or whatever?
pcmciautilities (same as above)
rmnologin (if i turn off, can i still login? i use auto-login in gdn)
screen
stop-read$ (not sure what this is, sudo sysv-rc-conf cuts it off)

also I have an hp printer... do i really need both of these?
hplip & cupsys

---

### Post by Dr. Nick on 2006-07-09
The pcmcia is the little laptop cards, If you have a laptop then leave them, if not you can probably disable it. Not sure on the others.

Just to calm you some, I havent ever disabled a service that has caused ubuntu not to boot, some things may stop working untill enabled again but ive never been locked out.

---

### Post by shawnrgr on 2006-07-10
Well i don't use any laptop cards, unless it also applies to things like my dvd-rom cd burner, but that came with the laptop. I don't have any expansion cards. so would that be safe to turn off?

---

### Post by scxtt on 2006-07-10
don't stop "loopback" / "mtab" / "rmnologin" ...

---

### Post by Dr. Nick on 2006-07-10
if you dont use any addon cards "the ones like credit card size" then pcmcia should be safe to disable. It shouldnt affect cd drives, if for some reason it did you could just re enable it.

---

### Post by ciscosurfer on 2006-07-10
To see a full list of your services (scripts) for each of your runlevels, issue the command(s):```
ls -l /etc/rcS.d   <---system boot scripts...be very careful here; if you accidentally disable a crucial service here, you may have to resort to a rescue disk to undo the mistake
ls -l /etc/rc0.d   <---shutdown/halt scripts
ls -l /etc/rc1.d   <---single-user mode scripts
ls -l /etc/rc2.d   <---multiuser mode scripts; by default, your GUI runlevel
ls -l /etc/rc3.d   <---multiuser mode scripts
ls -l /etc/rc4.d   <---multiuser mode scripts
ls -l /etc/rc5.d   <---multiuser mode scripts
ls -l /etc/rc6.d   <---reboot scripts
```So, with all of this in mind, you can see that one of the scripts under /etc/rcS.d is in fact the **readahead **script which allows the user to specify a set of files to be read into the page cache to accelerate first time loading of programs, typically during the boot sequence.  The system scripts at boot-time that are under /etc/rcS.d are actually twofold: **readahead **and **readahead-desktop**.  Now let's look at /etc/rc2.d which shows us that the script **stop-readahead **is enabled.  Some extra info:  If the script is preceded by an "S" then *init *starts the scripts when it goes through the runlevel.  If the script is preceded by a "K", then the script stops (kills) the script when it changes to a different runlevel.  If the script begins with a "D", then the script is disabled and *init *ignores it.

The bottom line here is you shouldn't change the **readahead **scripts as they are setup to enable a faster boot process for you: to start them at boot-time, and to squash them at "GUI-login-time."  Too much info for you?  Maybe.  But at least now you understand a little more about runlevels, where to find them on your system, and at the very least, what that pesky **readahead** was all about! :wink:

---

### Post by kpkeerthi on 2006-07-10
[http://doc.gwos.org/index.php/Speed_up_boot](http://doc.gwos.org/index.php/Speed_up_boot)

---

### Post by shawnrgr on 2006-07-10
thanks for all the info. so I should be able to safely shut down the pcmcia services but leave rmnologin, loopback, and mtab. so what about the rest?

screen
stop-read$ (not sure what this is, sudo sysv-rc-conf cuts it off)

also I have an hp printer... do i really need both of these?
hplip & cupsys

---

### Post by ciscosurfer on 2006-07-10
I explained what **stop-read$ **(**stop-readahead**) is a few posts back. [-X

---

### Post by shawnrgr on 2006-07-12
ahh yes my apologizes. ok thank you very much, i will leave them on. so what about these. these are the last ones that I can't find info on.

screen 
sendsings
single
stop-boot

---

### Post by ciscosurfer on 2006-07-13
nhnf = **n**o **h**arm, **n**o **f**oul (won't speed up the process)
-------------
**screen** = Script to remove stale screen named pipes on bootup {nhnf, but your choice}
**sendsigs** = Kills all remaining processes {leave this in place as is}
**single** = Executed by init[8] upon entering runlevel 1 (single-mode) {sends the TERM signal, then KILL signal, then enters runlevel 1; I'd leave it alone in case you need to enter a text-based terminal session to troubleshoot or the like}
**stop-bootlogd** =   Short-Description: starts | stops bootlogd to log boot messages; it's one of the first scripts to be executed. If this script is called as "stop-bootlogd", it will stop the daemon instead of starting it even when called with the "start" argument. {leave alone if you care about bootlog messages; helpful when troubleshooting problems.  Otherwise, nhnf}

---

