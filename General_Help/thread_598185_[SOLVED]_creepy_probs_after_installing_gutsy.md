---
title: "[SOLVED] creepy probs after installing gutsy"
date: 2007-10-31
forum: General Help
---

### Post by StevenRoose3 on 2007-10-31
i had feisty and after the upgrade, i hadn't any problems.
i was trying to get hibernate and standby working and because of something i did wrong, ubuntu "crashed."
(i was installing new graphic card: nothing came on the screen when rebooting)

now i reinstalled ubuntu gutsy, and when i try to boot i again see nothing.

when i boot into recovery mode and type *gdm*, i get the GNOME login screen.
when i login, i get :
[I]Internal Error
Failed to initialize HAL![/I]

a alert baloon opens about " new restricted ..." (i think manager but i forgot :p)
i click on it and see another one that isnt in use: ATI ...  (i have an ATI graphic card)
i try to use it, but i need a package : xorg-...-...

i tried to find it in the synaptic package manager, but i saw i haven't an internet connaction (while the internet cable was in the computer)

i tried to open network config (configuration) but i hadn't permission (like the error said)
i typed the command with sudo, but i still hadn't permission.

so, without internet, no update, no HAL fixed. no working HAL (to config network), no internet
=> looks like a loop.

someone any idea to fix it.
i cant do anything on my ubuntu now, and windows is very boring
::p

Steven

---

### Post by StevenRoose3 on 2007-10-31
dunno how, but by just trying very much things explained here about HAL
but i fixed that i could open network manager and so i can download packages now.
the HAL prob and boot prob still being

plz send links to threads.

Steven

---

### Post by computer_user_au on 2007-10-31
Hiya, 

I am having the same problems, "Failed to initialize HAL" on startup and no network connection.
As a workaround, try issuing this command:
```
sudo /etc/init.d/dbus restart
```
This command should be a temp fix.

The check out this link:
[http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL]("http://ubuntuforums.org/showthread.php?t=583940&highlight=HAL")

Try the above fix at the end of the first page... shld correct the problem.

Good luck....

---

### Post by computer_user_au on 2007-11-01
Also, check out:
[https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931]("https://bugs.launchpad.net/ubuntu/+source/dbus/+bug/25931")

I manually did the following on my system:

```
sudo mv /etc/rc2.d/S50dbus /etc/rc2.d/S12dbus
```

rebooted and the system worked, no more "Failure to initialize HAL" error messages and my network connection is working well.

---

### Post by StevenRoose3 on 2007-11-02
i had already S12 dbus.

but when i was looking in that folder, i saw something interesting that maybe is the way to fix another problem. the problem at startup, i have black screen... i have to run recovery mode and type gdm to start normally. so gdm doesn't start on startup and the 
S14gdm file is the only file that is no shortcut to a shell script!!!
maybe it have to be this way, but i found it weard.
can someone plz check what type of file ur SxxGDM is, when it is a shortcut, maybe also say what file he cuts short...

thanks for the hint :p

Steven
edit: i also finds this:
i error log file from nautilus:
===== BEGIN MILESTONES =====
0x81706a0 2007/10/31 20:30:21.9955 (GLog): Cannot connect to system bus: org.freedesktop.DBus.Error.FileNotFound : Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
0x81706a0 2007/10/31 20:30:21.9957 (GLog): Could not initialize hal context

0x81706a0 2007/10/31 20:30:21.9978 (GLog): Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
0x81706a0 2007/10/31 20:30:28.2305 (USER): debug log dumped due to signal 11
0x81706a0 2007/10/31 20:30:28.2308 (USER): debug log dumped due to signal 11
==> this last 2 lines continue more than 300 times.
but maybe here someone can find a reason fr my Failed to initialize hal problem, i tried every hal-fix thread here but not one helped
:(

---

### Post by computer_user_au on 2007-11-07
Hi...

Output of ls -la of /etc/rc2.d/ shows the following:
```
lrwxrwxrwx   1 root root    14 2007-09-17 18:24 S12dbus -> ../init.d/dbus
lrwxrwxrwx   1 root root    13 2007-10-31 22:52 S12hal -> ../init.d/hal
lrwxrwxrwx   1 root root    13 2007-04-20 14:00 S13gdm -> ../init.d/gdm
```

rgds...

---

