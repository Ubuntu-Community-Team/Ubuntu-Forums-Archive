---
title: "can't get gparted working"
date: 2017-09-11
forum: General Help
---

### Post by aartjansen on 2017-09-11
```
aart@xubuntu:~$ gparted
The program 'gparted' is currently not installed. You can install it by typing:
sudo apt install gparted
aart@xubuntu:~$ sudo apt install gparted
[sudo] password for aart: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gparted is already the newest version (0.25.0-1).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
aart@xubuntu:~$ gparted
The program 'gparted' is currently not installed. You can install it by typing:
sudo apt install gparted
aart@xubuntu:~$ 

```
Umm, I'm new to this, but this shouldn't happen right?

---

### Post by speartip on 2017-09-11
You can't start gparted from a terminal like that, as it requires root privileges.
gparted is also a gui program. If your using Xubuntu, check for it in your menu under settings.

---

### Post by vasa1 on 2017-09-11
In at least some flavors, gparted is removed as part of the installation process. So it may not be unusual to see```
The program 'gparted' is currently not installed. ...
```

---

### Post by Bucky Ball on 2017-09-11
> **speartip said:**
> You can't start gparted from a terminal like that, as it requires root privileges.

It should, in fact, start with just the command 'gparted', but you will be notified that gparted is running without root privileges, so bit pointless (you need them to do much). 

You could try 'gksudo gparted' to open a GUI with root privileges, but you may get the same result as you already get as this looks like a different problem. Not sure what.

---

### Post by aartjansen on 2017-09-11
If I try gksudo gparted, I get the prompt for the password, and then returned to the terminal.
If I search the menu for gparted it finds nothing.

All I really want to do is scan a NTFS HDD in a USB 3.0 dock. I might just boot into windows and do it.

---

### Post by gedakc on 2017-09-13
You might try forcing a reinstall with:

[FONT=Courier New]sudo apt-get install --reinstall gparted[/FONT]

---

### Post by irv on 2018-02-07
Has this problem ever been solved?
I have the same problem on two different laptops that have been upgraded to 17.10.1.
I tried to do a reinstall and run it from a command prompt: here is what I get:
```
sudo apt install --reinstall gparted
[sudo] password for irv: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnih-dbus1
Use 'sudo apt autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 449 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu artful/main amd64 gparted amd64 0.28.1-0ubuntu1 [449 kB]
Fetched 449 kB in 0s (1,478 kB/s)
(Reading database ... 181884 files and directories currently installed.)
Preparing to unpack .../gparted_0.28.1-0ubuntu1_amd64.deb ...
Unpacking gparted (0.28.1-0ubuntu1) over (0.28.1-0ubuntu1) ...
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3) ...
Processing triggers for bamfdaemon (0.5.3+17.10.20170810-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for man-db (2.7.6.1-2) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu5) ...
Setting up gparted (0.28.1-0ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.17-1) ...
irv@irv-Q500A:~$ sudo gparted
Created symlink /run/systemd/system/-.mount &#8594; /dev/null.
Created symlink /run/systemd/system/boot-efi.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-1000.mount &#8594; /dev/null.
Created symlink /run/systemd/system/run-user-121.mount &#8594; /dev/null.
Created symlink /run/systemd/system/snap-core-3887.mount &#8594; /dev/null.
Created symlink /run/systemd/system/snap-slack-4.mount &#8594; /dev/null.
Created symlink /run/systemd/system/tmp.mount &#8594; /dev/null.
Invalid MIT-MAGIC-COOKIE-1 key
(gpartedbin:9158): Gtk-WARNING **: cannot open display: :0
Removed /run/systemd/system/-.mount.
Removed /run/systemd/system/boot-efi.mount.
Removed /run/systemd/system/run-user-1000.mount.
Removed /run/systemd/system/run-user-121.mount.
Removed /run/systemd/system/snap-core-3887.mount.
Removed /run/systemd/system/snap-slack-4.mount.
Removed /run/systemd/system/tmp.mount.
irv@irv-Q500A:~$ 

```
Is this an issue with this release?

---

### Post by irv on 2018-02-07
I notice the line > Invalid MIT-MAGIC-COOKIE-1 key Not sure what this means?
I am having the same problem with UNetbootin. If I try to run it I get this.
```
irv@irv-Q500A:~$ sudo unetbootin
Invalid MIT-MAGIC-COOKIE-1 keyunetbootin: cannot connect to X server :0
irv@irv-Q500A:~$ 
```
Which seems to be the same problem.

---

### Post by irv on 2018-02-07
My problem is solved, it is the server problem. Wayland is the default and if I switch back to Xorg they both work. Maybe the OP should mark this one as solved.
Here is a good article on this and how to switch between Wayland and Xorg.
[https://itsfoss.com/switch-xorg-wayland/]("https://itsfoss.com/switch-xorg-wayland/")

---

