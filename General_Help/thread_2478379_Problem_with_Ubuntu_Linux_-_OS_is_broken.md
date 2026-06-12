---
title: "Problem with Ubuntu Linux - OS is broken"
date: 2022-08-25
forum: General Help
---

### Post by pleat6873 on 2022-08-25
20.04.4 LTS (Focal Fossa)


Seems like I derailed my OS somehow.


I believe it started when I ran `sudo apt install gedit-plugin-multi-edit` to install multi edit for gedit, and got up from my computer. When I came back there was much more text than I expected in the terminal - unfortunately I did not record it.


The machine seems to run but now nautilus is gone; so is settings, Ubuntu updater, and it seems Ubuntu software is not running either. 


I also got an error upgrading my apps:


```
user@computer:~$ sudo apt update && sudo apt upgrade
Hit:1 http://us.archive.ubuntu.com/ubuntu jammy InRelease                      
Hit:2 http://us.archive.ubuntu.com/ubuntu jammy-updates InRelease              
Hit:3 http://security.ubuntu.com/ubuntu jammy-security InRelease               
Hit:4 http://us.archive.ubuntu.com/ubuntu jammy-backports InRelease 
Hit:5 https://brave-browser-apt-release.s3.brave.com stable InRelease
Hit:6 https://updates.signal.org/desktop/apt xenial InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
1459 packages can be upgraded. Run 'apt list --upgradable' to see them.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libwacom9 : Depends: libwacom-common (= 2.2.0-1) but 1.3-2ubuntu3 is to be installed
E: Broken packages

```

How do I troubleshoot and fix this?

---

### Post by deadflowr on 2022-08-25
You say 20.04 focal, but your sources say 22.04 jammy.
Did you mean to change your sources?
What does
```
lsb_release -a
```
show?
This should show whether or not you are still on focal, and only the sources changed, 
or if you upgraded, at least partially, to jammy.

Though it does show you have over 1400 packages that are marked as upgradeable I would assume it hasn't done anything, yet.

---

### Post by miguel001 on 2022-08-25
*sudo apt install gedit-plugin-multi-edit* by itself shouldn't have caused any issue. That's a brain dead thing. If I was booted into the OS right now I'd do it and nothing bad would happen.

Its been too long but there's a way to force all packages to get fixed. You may have to look it up. I can't remember anymore.

Obviously, just clean installing is a way to go though.

---

### Post by pleat6873 on 2022-08-25
20.04.4 LTS (Focal Fossa) was the output from ```
cat /etc/os-release
``` in the terminal

I don't know what caused it but ```
apt install gedit-plugin-multi-edit
``` was the last Terminal command before the problem started. The computer locked from inactivity and just says authentication error now so I guess I'll have to just reinstall.

---

### Post by deadflowr on 2022-08-25
Seems likely only your sources were changed; how? unknown.
Not enough information.
Could probably be rectified by switching the sources back to focal.
> The computer locked from inactivity and just says authentication error now so I guess I'll have to just reinstall.
Can you restart/reboot or shutdown/boot it it?

---

### Post by TheFu on 2022-08-25
apt saves the CLI output in a history file in the log directory, somewhere.

Of course, if you have a good system backup, then use your restore process to get back where you were prior to running the command.  Backups have lots of uses.
If not, I'd boot from an "Ubuntu Install" or "Try Ubuntu" flash drive, backup all the data and settings I was unwilling to lose, then do a fresh install.  That's about 15 minutes, so it shouldn't be a big deal.  Then put the data and settings back.   Personal settings can be in the HOME.  System settings are a little tougher, since not all should be restored into a new install. Doing so will break it.

---

