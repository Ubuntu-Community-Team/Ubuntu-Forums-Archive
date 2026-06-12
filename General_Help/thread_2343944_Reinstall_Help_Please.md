---
title: "Reinstall Help Please"
date: 2016-11-21
forum: General Help
---

### Post by Quarkrad on 2016-11-21
I'm having trouble with Software Updater not working and decided to reinstall 16.04 - fortunately I have separate / and /home partitions so hopefully I should get this sorted/fixed quickly.  However, determining what I have installed since the initial install is a little confusing.  I have seen/used several terminal commands that lists (what seems hundreds/thousands) of packages - but to me this is far too detailed.  I could look in /home (hidden files) that gives me some indicators e.g. .dropbox, ,scribus, .hplip.  Is there a 'simpleton' way of finding out, not what packages you have installed, but applications over and above the basic install (not things like restricted-extras or build-essential)?

---

### Post by HermanAB on 2016-11-21
The dpkg --get-selections or apt list --installed command will list all packages.

You can save that in a file and then use the file with apt-get install, to ensure everything is installed again.  The tool is smart enough to skip things that are already there.

A little googling will find you an example.

---

### Post by vasa1 on 2016-11-21
> **Quarkrad said:**
> ...  Is there a 'simpleton' way of finding out, not what packages you have installed, but applications over and above the basic install (not things like restricted-extras or build-essential)?
IIRC, way back (12.04?) the software center had an option to list the history of what was added/removed *after* the original installation.

A more painful way is to go through the apt/dpkg logs (and archived logs) in /var/logs.

---

### Post by Bucky Ball on 2016-11-21
Just one thing: what gives the impression reinstalling is going to fix the Software Updater?

Might it not be better to post about the Software Updater issues? Other people have had issues with it, too, so there's other threads about. One might hold a solution. Maybe have a [look through some of them here]("https://ubuntuforums.org/search.php?searchid=13785837") which shows titles related to your *actual* issue: Software Updater not working. As you've posted no details about the actual problem with Software Updater, impossible to get specific.

Can you open a terminal and update like this in 16.04?

```
sudo apt update
sudo apt full-upgrade
```

The last command will *_not_* upgrade the OS to 16.10. Do you get any errors from either of those commands? If no errors, it is the Software Updater app itself and NOT your system so a reinstall would be overkill and, as I say, may have no effect whatsoever on your issue. (A reinstall is not a guaranteed fix.)

Just to get this clear: you are running 16.04, the Software Updater stopped working so you intend reinstalling 16.04 to fix it?

---

### Post by ajgreeny on 2016-11-21
This is not quite what you want, but using command ```
grep -i " install " /var/log/dpkg.log.1 /var/log/dpkg.log
```will list all packages that have been added since you installed the OS.
It lists absolutely every package, including all dependencies etc etc, so will be a long list, but many of them will be lib packages that you have probably not specifically chosen to add but were dependencies, so you could ignore most, if not all of those.

That might give you a chance to get some clues.

---

### Post by Quarkrad on 2016-11-21
I do have a thread **Software Update Crash** on my issue but so far I haven't solved it - been installing ubuntu since 8.04 using the same (basic/default) settings, this is the first time I've come across this. (Also happening on other friends laptops/Desktops I look after).  At the moment this Desktop is sitting on 284Mb of updates (shown when I manually launch Software Updater) - question is, why is the Updater not kicking in automatically (like it always has done) telling me there are updates to install?  I'm OK, but for family/friends who are not that savvy, the auto launching updater is the way to go.  I'm hoping that re-installing OS will get things back to how they should be - hence my decision to re-install rather than keep waiting to find out what has gone wrong.

---

### Post by Dennis N on 2016-11-21
> (Also happening on other friends laptops/Desktops I look after). At the moment this Desktop is sitting on 284Mb of updates (shown when I manually launch Software Updater) - question is, why is the Updater not kicking in automatically (like it always has done) telling me there are updates to install?

This is good to learn that many others are affected by this notification problem. I am seeing the same on 3 computers (all Xubuntu 16.04). I did make some posts myself at the end of your other thread, and that testing is ongoing at this time. 

I do have an Ubuntu MATE 16.04 that I don't use much. Possibly it is also affected. I should have to look at it too.

---

### Post by #&amp;thj^% on 2016-11-21
> **Dennis N said:**
> This is good to learn that many others are affected by this notification problem. I am seeing the same on 3 computers (all Xubuntu 16.04). I did make some posts myself at the end of your other thread, and that testing is ongoing at this time. 

**I do have an Ubuntu MATE 16.04 that I don't use much. Possibly it is also affected**. _**I should have to look at it too**_.
It is on my machine (Affected)..And also on Yackkety Mate (16.10)
I have never thought of this being an issue though...I have just preferred the terminal to upgrade && update. (But that is just my preference) :D
Kind Regards

---

### Post by Dennis N on 2016-11-21
> **1fallen said:**
> It is on my machine (Affected)..And also on Yackkety Mate (16.10)

Thanks for the input. Valuable information. I was wondering if it might have been fixed in 16.10 release (I haven't installed it to see).

---

### Post by Quarkrad on 2016-11-21
I have done the re-install but then realised it was probably a waste of time as I only reinstalled / - the problem may lay somewhere in a settings in /home.  Anyway - reinstalled / and still the same; perhaps a moderator could delete or merge this thread with my other thread on the specific notification issue.

---

### Post by Dennis N on 2016-11-22
More information from a previous look at automatic update checks and notifications can be found in my older thread where I first investigated this briefly in July 2016. Anything further I find I will probably add there rather than in someone else's thread.  

See: [https://ubuntuforums.org/showthread.php?t=2330407](https://ubuntuforums.org/showthread.php?t=2330407)

---

