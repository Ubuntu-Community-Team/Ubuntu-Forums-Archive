---
title: "Run root command at session start?"
date: 2017-11-28
forum: General Help
---

### Post by timonoj on 2017-11-28
Hi guys, I want to run a mount command as root right after user logs in. 
That's because this is a laptop and I need to wait until wifi is up and connected, in order to do an NFS mount. I do this, because the KDE pseudo-mounting that you can do from Dolphin has huge flaws when actually handling files, like...not being to open/play them. But that's another story. I'd just like to run the mount command as root as I finish the session login...Is there a way to automatically run it in the background, without having to prompt for a password etc? 

So far I managed a cronjob that waits for 7 seconds, does a ping, and if it responds, mounts the share. But it depends heavily on you logging in on the scheduled time window, otherwise it will fail, as cron will run regardless you're logged in or not, and the wifi only connects during the session start. I'd like something that runs exactly when it's already safe to mount it (after user logs in, and network manager automatically connects to the current wifi at session start).

Thanks a lot!

---

### Post by timonoj on 2017-11-29
Hmm I found a different easier way. I can leave the path defined in /etc/fstab with the 'user' option, and users are then allowed to mount the already listed path in their dolphin. However we're prompted for password the first time we do so. Bear in mind, this is an NFS share, so no credentials needed in that way. Any idea of what causes the credentials prompt?

---

