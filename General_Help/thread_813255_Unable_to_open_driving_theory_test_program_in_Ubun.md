---
title: "Unable to open driving theory test program in Ubuntu"
date: 2008-05-30
forum: General Help
---

### Post by pjpeter on 2008-05-30
I brought the official DSA theory test CD, although wine has allowed me ot install the program; I am unable to launch it.

PLease help, as I will regret to install windows on second hard drive.

---

### Post by antoniofh on 2008-05-30
I can't help you with the Wine issue as I've never used it. I can however recommend you look into a program called VirtualBox (virtualbox.org). It's an open source virtualization project that will allow you to install MS Windows that will run inside your Linux (Ubuntu) session. There is even a copy already in the Ubuntu repo's so you don't have to worry about compiling it on your own.

I use this project on my work PC under Ubuntu 8.04 because among my duties are desktop support for our windows XP users... this allows me to check errors and test software without having to reboot, like you would with a dual-boot system. So far any software I've attempted to install has worked just as it would in a standard windows installation... which is not something I've ever heard from a Wine user.

I've attached a screenshot of it running on my system...

---

### Post by Zorael on 2008-05-30
Not to mention it can be run and seamlessly blend with your normal environment.

[http://www.youtube.com/watch?v=hBz0ZTiwo-I](http://www.youtube.com/watch?v=hBz0ZTiwo-I)

To answer your original question though; wine doesn't run everything. It tries its best but the fact remains that Windows programs were ultimately written for Windows. You can check [http://appdb.winehq.org](http://appdb.winehq.org) for a database of programs and how well they work. If your program is [http://appdb.winehq.org/objectManager.php?sClass=application&iId=6246](http://appdb.winehq.org/objectManager.php?sClass=application&iId=6246) it seems to be tagged as 'garbage', which isn't promising.

Virtual machines - such as VirtualBox - works great for those programs that otherwise can't be run under wine, *provided* that they don't require any special hardware access. This means no 3d acceleration, no iTunes connecting to your iPod through USB (yet), etc. In most cases, these can be replaced with linux-native open source software. Such as Amarok/gtkpod/Banshee/etc for iPod management.

edit: If iTunes, Photoshop and other notorious doesn't-work-well-or-at-all-under-wine apps were open source, there'd certainly be an effort to make them work on all platforms. But as it is, they're proprietary, and their authoring companies are content to keep it Windows/Mac-only, at the expense of us users.

---

