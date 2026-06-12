---
title: "Changing server-kernel to 386-version"
date: 2007-02-22
forum: General Help
---

### Post by Arandil on 2007-02-22
Since the search has no related topics to "change server kernel to 386", I'm posting this here.

I wanted to install Ubuntu Sever 6.10 on my VIA Epia board last night. All went well, installation happened in a flash. However, after GRUB gives the boot-command, my system reboots and gets stuck in an infinite loop. Appearantly this has something to do with server-kernel not being suitable for the C3-procesor. More information can be found here : []("http://rick.vanrein.org/blog/software/ubuntu-grubreboot-c3.2006-12-23-16-03.article")

Now I was wondering how to achieve this. Something with a LiveCD and "chroot", but I'm not so sure. If anyone could help me with some simple steps, it would be much appreciated!

---

### Post by markitect on 2007-03-01
Boot off a live cd, then open up a terminal
find where your installation is located and make sure its mounted, the type in chroot and the top level of your root partition, now inside the chrooted terminal everything you do will be based on your setup so you can do you ```
su username 
sudo apt-get install linux-image-386
``` and use the password and username you made during the install.  Then exit twice to get out of the terminal and reboot.

chroot literally changes the root that the terminal is working from so all changes in packages, config etc will affect your install.  Please note that if you have boot or etc as other partitions you will need to make sure those get mounted.

---

