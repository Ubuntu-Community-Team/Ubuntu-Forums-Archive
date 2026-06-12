---
title: "Gutsy file permissions problem"
date: 2008-03-26
forum: General Help
---

### Post by n30nex on 2008-03-26
No matter how I try to get into it, my xorg.conf is locked out to me.

sudo gedit and gksu gedit do nothing, they allow read but not write access.

logging in as root in terminal without x running, still tells me that i cant save anything under nano because it was denied.

so any reason why both root and the admin cannot edit xorg? I'm just trying to revert back to an old backup of it [xorg.conf_backup2] but,

sudo cp blah blah blah, does not allow me to copy the file contents, its all just more permission denied.

The admin IS in the admin group, and the file does say it belongs to root and root alone.

How come root or sudo root cannot access this?

---

### Post by warp99 on 2008-03-26
Check the file permissions to the left of the file using the ls -l command:

```
-rw-r--r-- 1 root root 
```

Does it look like this? if not just change the permissions:

```
sudo chmod 644 xorg.conf
```

Then you should be able to edit the file as root using sudo. :)

---

### Post by n30nex on 2008-03-26
Well thats a problem.

```
-rw-r--r-- 1 root  root   3706 2008-03-25 16:11 xorg.conf
```

```
neonx@neobox:/etc/X11$ sudo chmod 644 xorg.conf
[sudo] password for neonx:
chmod: changing permissions of `xorg.conf': Operation not permitted
neonx@neobox:/etc/X11$
```

---

### Post by warp99 on 2008-03-26
Well you have a different problem since you lost sudo access. This thread has the information you are looking for:

[http://ubuntuforums.org/showthread.php?t=14050](http://ubuntuforums.org/showthread.php?t=14050)

---

### Post by n30nex on 2008-03-26
I did not change my username, and im still listed as one of the sudoers.

This is very confusing.

---

### Post by warp99 on 2008-03-26
Try the command 'groups neonx' to see that you are in the admin group. If not we have to add you while in root.

---

### Post by n30nex on 2008-03-26
```
neonx : neonx adm dialout cdrom floppy audio dip video plugdev scanner lpadmin admin netdev powerdev
```

---

### Post by warp99 on 2008-03-26
Try typing 'sudo bash' and see if you change the user to root and try to edit the file xorg.conf. Here is some more information on using sudo and root that may help:

[https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d](https://help.ubuntu.com/community/RootSudo#head-6357ee1f3ec93078a7d7cbc2c627208117e9499d)  

If you can't do that you could boot into root during grub and add a new user to the sudoers file list, you may have a corrupted password file. :(

Edit:

You can also check out this guide:

[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

### Post by n30nex on 2008-03-26
Ok, so my user is in all the required groups, and i can sudo other commands, but i still cannot edit or replace xorg.conf as this user or even as root, tells me operation denied.

This happens in terminal, nano, gedit and recovery.

EDIT:

This is what sudo bash will do:

```
neonx@neobox:~$ sudo bash
[sudo] password for neonx:
root@neobox:~# sudo gedit /etc/X11/xorg.conf
root@neobox:~# sudo dpkg-reconfigure -phigh xserver-xorg
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080326223109
mv: cannot move `/etc/X11/xorg.conf.dpkg-new' to `/etc/X11/xorg.conf': Operation not permitted
```

---

### Post by n30nex on 2008-03-27
bump, please, I appreciate all help given.

Does this help?

[IMG]http://i52.photobucket.com/albums/g38/neonx/Screenshot.png?t=1206634188[/IMG]

---

