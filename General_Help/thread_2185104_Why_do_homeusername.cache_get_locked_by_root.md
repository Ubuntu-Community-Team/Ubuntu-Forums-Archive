---
title: "Why do /home/username/.cache get locked by root?"
date: 2013-11-01
forum: General Help
---

### Post by Pako Pako on 2013-11-01
Just performed a shutdown/reboot in Xubuntu 12.04 LTS and when I got back, I had difficulty opening up Firefox, Software Center, and a bunch of stuff. Usually a log file was missing, a profile couldn't be found, and general input/output errors. Long story short, I found that the power-down was treated as an "improper crash" by Software Center and Firefox (both of which, should have been closed) and were locked by root. Why did that happen?

To expand: I did some digging and found that somehow root had possession of some folders. I double-checked this with Firefox (version 23) -- some files in /home/user/.mozilla/firefox/.default/ were locked by root. Using *CHOWN -R user:user* would only be a temporary fix until I ran Firefox again (which would have root repossess the files). I could *sudo firefox* from the CLI with no issues; it would even restore my last session.

Searching for more root-only folders in my home/user directory, I found a bunch in /home/user/.cache -- in fact, the **software-center** was no longer owned by user:user. Removing it with *rm -rf* gave me back Software Center (which was a relief, because *sudo apt-get clean* wasn't getting me anywhere). Removing the mozilla folder in .cache gave me back Firefox.

My questions are:

[LIST]
[*]Why did these cache folders cause issues with running these programs?
[*]Why were these cache folders under root instead of user?
[*]Why don't these files get flushed upon shut-down?
[/LIST]

---

### Post by steeldriver on 2013-11-01
[LIST]
[*]because the application want to write there, and when run as a normal user it can't if the directory is owned by root (at least not with the default umask) 
[*]in the case of GUI applications, most likely because at some point you ran them with sudo - if you need to run a GUI application with elevated privileges you should always use gksudo (or kdesudo under KDE-based sessions) because plain sudo doesn't necessarily set all the appropriate environment variables 
[*]because the purpose of cache files is to provide persistence across user-sessions (including across reboots) 
[/LIST]

---

### Post by tgalati4 on 2013-11-01
The disk may have had problems and when a *fsck* was performed upon reboot, some errors were cleaned up, resulting in root permissions in files and directories that were affected.

The cache structure of firefox is called a profile.  Sometimes, after a long time (several months), your profile grows huge and gets balled up.  Sometimes you can clean this up within firefox by doing a "clear cache, clear cookies, clear history".  If you don't manually perform this housecleaning, firefox will slow down and eventually crash.  It's possible that the shutdown was interrupted because this cache became too large or it became corrupt.

Your options are limited.  You can delete the cache directory completely, which then means you are starting fresh, or you can try to clean up things internally using the tools within firefox.

The fact that several directories were affected (like the software-center/apt cache) points to a disk problem.

What are the SMART properties of the disk?

---

### Post by Pako Pako on 2013-11-01
> **steeldriver said:**
> in the case of GUI applications, most likely because at some point you ran them with sudo - if you need to run a GUI application with elevated privileges you should always use gksudo (or kdesudo under KDE-based sessions) because plain sudo doesn't necessarily set all the appropriate environment variables
Crap. I think I did this with File-Roller at some point. That might be why it won't remember window size or positioning unless I run as "sudo file-roller".

Have any ideas on resetting the environment variables for File-Roller/Archive-Manager? A reinstall doesn't quite do the trick, nor does a complete uninstall from Synaptic Package Manager. (Because file-roller is also a plugin for Thunar under XFCE goodies, I could reinstall that... but that means removing *everything* from the goodies folder...)

> **tgalati4 said:**
> The disk may have had problems and when a *fsck* was performed upon reboot, some errors were cleaned up, resulting in root permissions in files and directories that were affected... The fact that several directories were affected (like the software-center/apt cache) points to a disk problem... What are the SMART properties of the disk?
The Disk Utility reads the drive as "Healthy." Endurance, Calibration Retry, Seek Error Rate, Reallocated Sector Count, Throughput performance, and Read Error Rate are all "good."

I might try deleting the "~/user/.cache" directory down the road. Nothing lasting should be in there, right?

---

### Post by steeldriver on 2013-11-01
or you could just make sure everything in it is owner:group you

```
sudo chown -R *user*:*user* ~/.cache
```

---

### Post by Pako Pako on 2013-11-02
Tried that, but somehow root was repossessing them. I gave up and began systematically sudo-removing folders. (I think getting rid of dconf fixed most window-positioning issues.)

So I didn't fully get why this happened, but I did manage to fix things. Thread closed.

---

