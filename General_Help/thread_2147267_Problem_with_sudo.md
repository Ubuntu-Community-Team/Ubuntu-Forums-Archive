---
title: "Problem with sudo"
date: 2013-05-21
forum: General Help
---

### Post by thebj on 2013-05-21
I am running 12.10 on my laptop. I tried to get rid of the need to enter password for shutdown command in terminal. I ran visudo and added the following line in the file:

%users ALL=(ALL) NOPASSWD: /sbin/poweroff, /sbin/reboot, /sbin/shutdownHowever, now when i use the sudo command in terminal, the following error message is displayed:

sudo: parse error in /etc/sudoers near line 33
sudo: no valid sudoers sources found, quitting
sudo: unable to initialize policy plugin

Now, i cant use sudo at all. Please help...

---

### Post by SlugSlug on 2013-05-21
Use a live disk and edit the file

/etc/sudoers

at the bottom of my file I have multiple lines for each command (not sure if thats the problem)

USERNAME ALL=NOPASSWD: /usr/sbin/iftop
USERNAME ALL=NOPASSWD: /usr/sbin/command

---

### Post by thebj on 2013-05-21
Wouldn't editing the file in the live cd only change it during the current session? Thanks

---

### Post by Impavidus on 2013-05-21
Mount the hard disk, modify the sudoers file present there, not the one in the live environment.

---

### Post by SlugSlug on 2013-05-21
edit the file on your hard drive. normally under /media I think once you have clicked it to mount it

---

