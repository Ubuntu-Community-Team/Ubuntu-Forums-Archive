---
title: "remastersys problem"
date: 2008-01-31
forum: General Help
---

### Post by svtfmook on 2008-01-31
remastersys seems to work fine.

however, when i try to run the livecd, at boot i get an error along the lines of it looking for $HOME=/home/[user]/, ect.

anyone know how to fix this?

---

### Post by pointone on 2008-01-31
Posting the exact error message would probably help us help you.

---

### Post by svtfmook on 2008-02-01
Your home directory is listed as /home/user but it does not appear to exist. Do you want to log in with the / (root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session

---

### Post by gilf on 2008-02-10
Similar problem here, A live DVD created with Remastersys asks for password with any command normally requiring a user password in an installed system. No password seems to satisfy it. Blank password doesn't work. Sudo command in terminal requires a password. Logging on as a different user doesn't work because it's a liveCD naturally and there is no Home directory for the new user. The error message posted by the OP appears if you try to login using the existing home.

In other words, unless I know what root's password in Ubuntu is, I'm unable to even install to HD.

---

### Post by gilf on 2008-02-10
Okay here's a clue:

> You should start with a clean install of Klikit, Ubuntu or variant and use a single user to make all changes.  You should not install any proprietary video drivers like the nvidia or ati drivers as they will not be used on the livecd and users will have to reinstall them after installation.  Clean up history and cache and copy over the contents to /etc/skel but be sure to change the ownership of everything in /etc/skel to root.  While the livecd/dvd is being created, you will not be able to open any other apps or windows.  It is highly recommended to become root to do this by issuing "sudo su" in a terminal window and then running "remastersys dist".  The reason for this is that the uid for the users on the system have to be changed to be below 1000 or the casper livecd scripts will not create the live session user properly.  Remastersys will restore the UID's back to their original values once it is finished.

---

### Post by gilf on 2008-02-11
Uupdate  /etc/apt/sources.list with 

> # Remastersys
deb [http://www.remastersys.klikit-linux.com/repository](http://www.remastersys.klikit-linux.com/repository) remastersys/

then reload

then upgrade Remastersys to latest.

The password problem is a bug.

Newest version has a GUI, as well

---

### Post by gilf on 2008-02-13
For some other consderations when trying to do an HD install from a remastered LiveCD, please read this:

[http://ubuntuforums.org/showthread.php?p=4321458#post4321458](http://ubuntuforums.org/showthread.php?p=4321458#post4321458)

---

