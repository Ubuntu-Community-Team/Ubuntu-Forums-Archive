---
title: "Rescue Mode network problems"
date: 2008-03-31
forum: General Help
---

### Post by nobujine on 2008-03-31
So i accidentally uninstalled about 25 packages (i guess they were important, ubuntu wont boot now) and have been trying to use the rescue mode to fix the problem.  I have an Ubuntu 7.10 alternate installer cd, and have been using the "rescue a broken system" to attempt repair.  So i boot into rescue mode using the cd, and create a shell in my partition, and all is well.  Since im not really sure what packages were uninstalled, i attempt to reinstall them using "sudo apt-get install ubuntu-desktop".  It determines it needs to install about twenty-five packages, and then attempts to download them, and can never connect to us.archive.ubuntu.com.

I have ran iwconfig and determined that the network card has an IP address, so all should be fine, and I am now stumped.

Yes, reinstalling is an option, but I would prefer to save the system I have, any help would be appreciated

---

### Post by cdenley on 2008-03-31
Can you ping your router? Can you resolve dns names (dig us.archive.ubuntu.com)?

---

### Post by nobujine on 2008-03-31
im on a college dorm network, and i connect via a switch in the room, but i pinged my default gateway, and it worked fine.

the "dig us.archive.ubuntu.com" command was a failure, it failed to reach any servers or some such.

---

### Post by cdenley on 2008-03-31
You could install the packages from the cd. You probably just have to uncomment a line at the beginning of /etc/apt/sources.list that starts with "deb cdrom:".
```
sudo nano /etc/apt/sources.list
```
Then
```

sudo apt-get update
sudo apt-get install ubuntu-desktop

```

Was your internet working with your switch before you removed those packages? Did you try it with a wired connection?

---

### Post by nobujine on 2008-03-31
i attempted to run the command "sudo nano /etc/apt/sources.list" and it said "error starting terminal: bterm" or something along those lines

i was at home (i go home on the weekends) where we have a wireless router, and the internet was actually out there, so i brought the laptop to school to fix it.  the internet has worked at the dorm all along.

---

