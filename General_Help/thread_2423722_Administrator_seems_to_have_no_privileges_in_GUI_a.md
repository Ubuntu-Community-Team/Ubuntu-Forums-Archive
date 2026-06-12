---
title: "Administrator seems to have no privileges in GUI apps"
date: 2019-07-28
forum: General Help
---

### Post by quintu2 on 2019-07-28
I am the administrator and only user of my system. I can no longer perform many actions in GUI apps: 1) I cannot install software from the software store ("Unable to download updates: you do not have permission to install software", 2) Backups will not perform automatic backups ("Backup failed: Not authorized to perform operation"), 3) In Settings -> Details -> Users, the Unlock button is grayed out and I can't unlock, 4) Clicking Restart or Power off in the top right corner do nothing.  I just switched to lightdm because gdm3 was crashing on login, and the timing makes me believe that switching to lightdm is connected to this issue.

However, I can perform everything normally from the command line with sudo. I tried installing policykit-1-gnome per the suggestion [here]("https://askubuntu.com/questions/970838/ubuntu-software-center-no-permission-to-install-software"), but it didn't change anything. I tried running sudo gnome-software, but it still won't let me install the software. (I'm trying to install cronopete, which is a .deb file, if that's relevant).



Running 19.04. Ran apt-get update and apt-get upgrade, so everything is up to date. Running "groups $USER" in the terminal returns sudo (among others).

---

### Post by TheFu on 2019-07-28
Welcome to the forums.

Don't use sudo to run GUI programs. If you must (you aren't listening to me), then use **sudo -H**, so permissions in your userid's HOME don't get screwed.  You can fix that issue, which you almost certainly have, by running
```
sudo chown -R $USER:$USER $HOME
```
That is the exact command. Those environment variable will work for the sudo-userid and the correct HOME directory.

If you want to install a program, stay within the package management system. Installing .deb files directly will lead to a broken package system in 3-6 months.  I've written about the preferred order for installing packages a few times in these forums.  The only worse way than using a .deb file directory is to use source.

I've never used gnome-software. It isn't even installed on my systems.
BTW, [https://launchpad.net/~rastersoft-gmail/+archive/ubuntu/cronopetedev](https://launchpad.net/~rastersoft-gmail/+archive/ubuntu/cronopetedev) seems to show that Cronopeate not updated since 14.04.  Using a PPA that old isn't good.  Perhaps there is a snap package or flatpack?

If you want a nice, easy to use, backup tool that is in the repos, check out back-in-time.  It has a GUI and uses rsync+hardlinks underneath. Many people find that method of versioned backups useful.  I ran it on Mom's computer for a few years.  I don't use it on my systems. Find GUI tools less-than-great for backups.

As for all the GUI issues you have having, if the chown command doesn't fix them all, create a new userid, add it to the sudo group, and use it. Bet that solves everything.

---

### Post by GhX6GZMB on 2019-07-28
++++1 to TheFu.

I'm a newbie to Ubuntu since some weeks, and have learnt the hard way that sudo and GUI don't mix well. I now finally have en error- and warning-free system that unfortunately has gone through many re-installations before reaching this point.
I now do a backup using TimeShift (a GUI interface to rsync) before I do any changes to my computer. I believe it's comparable to back-in-time. Trick is, they backup all the configuration files, which are always a pain to recreate.

---

### Post by quintu2 on 2019-07-28
Hi TheFu, thanks for all of your suggestions & help.

I tried your ```
sudo chown -R $USER:$USER $HOME 
``` command, but it didn't change anything. I also created a new user, added it to sudo, but am still experiencing the same behavior. Could it be that polkit is somehow not functioning correctly? I'd prefer not to do a fresh ubuntu install, but it's not the end of the world if that's the easiest fix.

---

### Post by TheFu on 2019-07-28
I have no clue about polkit. Never use it myself. 
You do it the way you need to do it.  The best way to learn stuff is by breaking it and having to fix it.  I've done that hundreds of times over the decades.

If you used sudo with GUI programs, there's no way to know what actually happened. Live and learn.

Adding a new user doesn't do anything if you don't logout and login using that new userid. ;)  I don't want to assume anything you didn't say.

---

