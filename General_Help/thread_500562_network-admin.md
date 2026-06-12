---
title: "network-admin"
date: 2007-07-14
forum: General Help
---

### Post by rkrizan on 2007-07-14
When trying to load network-admin, I'm getting an error message: 

The configuration could not be loaded  
You are not allowed to access the system configuration.

Thats giving the proper root/admin password as well. I've also tried running it as root, of course. Getting rather odd error messages:

root@pharaoh:~# network-admin

(network-admin:6035): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

(network-admin:6035): Liboobs-WARNING **: There was an unknown error communicating with the backends: Process /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl exited with status 2

(network-admin:6035): Liboobs-WARNING **: There was an unknown error communicating with the backends: Process /usr/share//system-tools-backends-2.0/scripts/SystemToolsBackends.pl exited with status 2
root@pharaoh:~# 


Any ideas how I can fix this?

---

### Post by rkrizan on 2007-07-14
Anyone have any ideas?

---

### Post by rkrizan on 2007-07-14
I tried uninstalling and reinstalling gnome-system-tools with apt, with no success. Any ideas?

---

### Post by kitty500cat on 2007-07-14
When logged in as an unprivileged user (not root), try this:
```
sudo network-admin
```

Please let me know if it works.

Regards :)

---

### Post by rkrizan on 2007-07-14
I've already tried all that. su, sudo, gksu, gksudo, etc. Nothing works. I can't even run Users and Groups, get the same error message.

---

### Post by kitty500cat on 2007-07-14
In that case, I have no idea.  Sorry I wasn't able to help.

Hope somebody else can help you get it figured it out.

---

### Post by mcook2 on 2007-07-26
I'm having similar problems with both gksu users-admin and gksu-network-admin.  I just get a blank window and I have to use the Force applet to kill the window in each case.  Afterwards I still see these processes listed when I do a ps -aux | grep <my_user_name>.

I get the same results using sudo gksu user-admin from a Terminal.

One time I actually got the "users" dialog box filled in but then it froze when I clicked on the "Groups" button.

This seemed to start after July 13th when my SPM History shows these updates were applied:

> Commit Log for Fri Jul 13 18:04:10 2007

Upgraded the following packages:
app-install-data-commercial (7.1) to 7.2
debootstrap (0.3.3.2ubuntu3) to 0.3.3.3ubuntu3~feisty1
gnome-btdownload (0.0.25-1ubuntu1) to 0.0.28-1~feisty1
hal (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
hal-device-manager (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
iptables (1.3.6.0debian1-5ubuntu2) to 1.3.6.0debian1-5ubuntu2.1
libgl1-mesa-dri (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libgl1-mesa-glx (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libglu1-mesa (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
libhal-storage1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libhal1 (0.5.8.1-4ubuntu12) to 0.5.9-1ubuntu2~feisty1
libnautilus-burn4 (2.18.1-0ubuntu1) to 2.18.1-0ubuntu1.1
libxvidcore4 (2:1.1.2-0.1ubuntu1) to 2:1.1.2-0.1ubuntu1.1~proposed1
mesa-utils (6.5.2-3ubuntu7) to 6.5.2-3ubuntu8
nautilus-cd-burner (2.18.1-0ubuntu1) to 2.18.1-0ubuntu1.1
python-launchpad-bugs (0.1.13) to 0.1.13.2

Installed the following packages:
hal-info (20070402-1ubuntu1~feisty1)

I seem to be short of any messages I could use to debug this.

Please can anyone suggest what my next step should be to try to resolve this problem. 

Here's my uname -r and arch info:

> uname -r
2.6.20-16-generic
arch
x86_64

My gksu package is Version 2.0.0-1ubuntu3.

Thanks,

Michael Cook

---

