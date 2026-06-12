---
title: "Cant login"
date: 2006-11-30
forum: General Help
---

### Post by tlinuxnub on 2006-11-30
I'm somewhat new to the linux scene. I've tried it before and had some bad luck and moved back to windows. But I thought I would give it another go.  Yesterday I downloaded the latest version of kubuntu and installed it on my sony vaio laptop.  Through the installation it never asked me to create a user name, but it did ask me for a password.  The installation has completed and im at the login, but the password doesn't do anything without a user account. Any work arounds for this? I'm completely at a loss cause I have never had this happen before. Thanks

---

### Post by cronholio on 2006-11-30
It's pretty unlikely that you haven't been asked for a username during installation. IIRC, there is a dialog asking your real name and the next thing it asks is a username.

If you can't remember what you typed in during installation, do a re-install (since the system is new anyway it won't make a difference).

There are workarounds using a Live CD but it is more painless to do a fresh install.

---

### Post by CatKiller on 2006-11-30
I vaguely remember seeing reports from confused new users that somehow managed to do an OEM install from the Alternate disk, and I think there's another step to actually set it up for normal use. Could that be what you've done? I don't know anything other than that, since I've not done it myself.

(EDIT: I think this came out sounding a bit nasty - I meant that I didn't know how to do an OEM install)

---

### Post by anaconda on 2006-11-30
Reinstalling might be a good idea, but here is an alternative:

Select "recovery mode" from grub-boot loader. This will log to text mode with root (admin) rights. then type:
```
adduser the_username_you_want admin
```
this will make a new user and asks you to set password for it.

other alternative is to find out the username that was created during install:
```
ls -la /home
```
the name of the directory in your home directory is the same than the username you created when installing....

then just type:
```
reboot
```
to reboot hte machine and log normally to ubuntu. you can log either with the new username or the old which you found out.

---

### Post by bapoumba on 2006-11-30
@ tlinuxnub : if you did install from the alternate CD, then your current login is : oem + passwd.

Just run **sudo oem-config-prepare**. Next time you'll boot up, you will be prompted to create a new login + pwd, the oem user will be deleted.

---

