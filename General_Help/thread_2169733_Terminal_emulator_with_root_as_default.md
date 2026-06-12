---
title: "Terminal emulator with root as default"
date: 2013-08-23
forum: General Help
---

### Post by LinuxUser666 on 2013-08-23
Hello fellow Linux users, I am running an Xubuntu 12.04 and have installed 3 terminal emulators....guake terminal, GNOME terminal and Xfce4 terminal. 
By default Ubuntu distributions require you to do ```
sudo
``` to execute something related to system or do ```
sudo su 
sudo -s
``` to grant myself root priviledges. My question is can I modifie any of these terminals to execute ```
sudo su
``` upon me opening them? And therefore have one terminal with constant root priviledges, while on others I have normaln juristiction.

My regards. :D

---

### Post by hakermania on 2013-08-23
Edit the .desktop file for your gnome-terminal and alter it to this:

```

gnome-terminal -e "bash -c \"sudo su; exec bash\""

```

It will ask you for password each time it starts.

---

### Post by Impavidus on 2013-08-23
Create a launcher with the command```
gksu xfce4-terminal
```or whichever one you want to use for that.

---

### Post by LinuxUser666 on 2013-08-24
Hey hakermania can I do that thing of yours so that I do not have to enter passwd every time, you know, can it memorise my passwd or something? Just curious... 

My regards.

---

### Post by JKyleOKC on 2013-08-24
Check out the manual page for visudo ("man visudo") to learn how to eliminate the need for the password -- but be warned that having the password requirement will probably save your system from damage someday, when you fat-finger a command and accidentally turn it into something that will destroy critical files!

You can selectively disable the password, for only specific commands, and that means you can create a script to launch the root-enabled script for you, make it executable, and then disable the password requirement for only that script.

You'll still be at increased risk when using your root-enabled terminal, though -- so be very careful when using it, and make sure you have up to date backups of all critical files.

---

### Post by LinuxUser666 on 2013-08-25
Yes I know, I am fully aware of possible risks of constant root, I am curious on possibility of using one of my many terminals as root constantly and because of the reason I most usually need it because of the work I do. But thanks for the warnings and concerns.

My regards. \\:D/

---

