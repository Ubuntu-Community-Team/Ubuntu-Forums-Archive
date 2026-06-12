---
title: "2 problems away from perfect harmony!"
date: 2008-03-22
forum: General Help
---

### Post by Islington on 2008-03-22
1)I need to sync a particular folder in my home partition, to a usb hdd that is usually always connected to the same computer.

Honestly I have no idea what to google here. so I will give a specific example:

I have a folder [Projects] on my desktop. I have a copy of this folder on my usb hdd (also called [Projects]). I need a way so that once I make some changes in the folder on my desktop, that change will be reflected in the folder on my usb hdd. 

2) I am very new to networking, and recently set up my first samba network, to share files across my LAN . There are 2 computers involved my huge in resources ubuntu box, and my slim xp notebook. The files sharing works beautifully as long as my laptop can wirelessly connect to my router. I need some way to access the files on my ubuntu box over the internet (for when I am at college).

I tried googling webserver, but got too many confusing results such as ftp/apache/samba(?). Please help me figure out what to do.

Honestly I am this close<->from being completely happy with my setup, please help me out.

---

### Post by banewman on 2008-03-22
To sync the files you need rsync - man rsync  in a terminal will let you know the options.
Over the net   ssh  is the recommended way to access comps.
[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)   - might help.
:)

---

### Post by Islington on 2008-03-22
> **banewman said:**
> To sync the files you need rsync - man rsync  in a terminal will let you know the options.
Over the net   ssh  is the recommended way to access comps.
[http://ubuntuforums.org/showthread.php?t=11808](http://ubuntuforums.org/showthread.php?t=11808)   - might help.
:)

thanks for such a fast response, after reading the rsync man page.. I can most probably tinker until I figure it out. For future reference, how did you know this command? rather.. how can someone find the relevant command, when so many are available?

after reading the net ssh link, I understood maybe 3%.. as my grandma said, time to hit the google.:)

---

### Post by banewman on 2008-03-22
I started with linux in 1998 and have learnt by wrecking alot of installs.
:)

---

### Post by KeyserSoze93 on 2008-03-22
have you got a firewall set up? probably best to set that up before file sharing over the internet. i use firestarter.

first install openssh-server

then configure port forwarding on your router (see the manual) for port 22 to your desktop pc.

then find the ip of where you are connecting from and add it to your firewall ([http://www.findmyip.com](http://www.findmyip.com) when you're there).

then find out your own ip (same applies).

finally, install WinSCP (assuming it's a windows computer) onto the computer you want to connect <b>from</b>.

then you can put your ip into winscp and access your files. works like a dream for me...

---

