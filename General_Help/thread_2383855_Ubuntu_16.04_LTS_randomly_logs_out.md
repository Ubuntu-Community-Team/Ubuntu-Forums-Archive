---
title: "Ubuntu 16.04 LTS randomly logs out"
date: 2018-01-30
forum: General Help
---

### Post by amaelith on 2018-01-30
I am currently running Ubuntu 16.04 LTS with dual boot (Windows 10 is my other OS) on a Dell Inspiron with a Nvidia GPU. While I am working on Ubuntu, the screen will suddenly go blank and show the log in screen before completely going black. Sometimes the login screen will reappear if I press the power button, however it'll usually continue doing this and the power button no longer is responsive. I found out that if I open and close the laptop the login screen will reappear. None of my applications are closed, I can resume where I left off but it is rather annoying to be constantly interrupted this bug.

I've tried going to the tty and deleting my Xauthority file and restarting, but this doesn't fix the issue. What commands I typed is listed below

```
sudo rm -v .Xauthority
sudo service lightdm restart
```

When I try to do the sudo apt-get update to see if that'll fix the issue, I get an error about a public key not being available.

```
sudo apt-get update
[sudo] password for <omitted>: 


Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Hit:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease             
Hit:3 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease           
Hit:4 http://security.ubuntu.com/ubuntu xenial-security InRelease       
Get:5 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease [17.5 kB]
Hit:6 http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu xenial InRelease
Ign:5 http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease
Hit:7 https://packagecloud.io/slacktechnologies/slack/debian jessie InRelease
Fetched 17.5 kB in 1s (11.0 kB/s)
Reading package lists... Done
W: GPG error: http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6A9653F936FD5529
W: The repository 'http://ppa.launchpad.net/atareao/atareao/ubuntu xenial InRelease' is not signed.
N: Data from such a repository can't be authenticated and is therefore potentially dangerous to use.
N: See apt-secure(8) manpage for repository creation and user configuration details.

```

---

### Post by tinylagarto on 2018-01-30
Regarding the first issue, what are your settings for power management? I suppose you use the Unity desktop and maybe you set that the screen goes blank and locks after a certain amount of time. 

The second issue is with a PPA. If you do not need the apps from there and it is quite a list for an external repository, you could remove the PPA from your system via the software properties program and try the update again.

---

### Post by amaelith on 2018-01-31
It doesn't have to do anything with my power settings since it'll just go blank while I am doing something that second. But I have it set in my settings where my display never goes off unless the laptop is closed.

---

