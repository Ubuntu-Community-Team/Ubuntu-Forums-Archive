---
title: "Problem with partitions trying a solution for grub"
date: 2017-06-19
forum: General Help
---

### Post by vimorcillo on 2017-06-19
Here the information about my partitions:
[http://paste.ubuntu.com/24900386/](http://paste.ubuntu.com/24900386/)

I tried to mount other partitions, repair with SuperGrub, with boot-repair and anything work fine, please help!

---

### Post by Bucky Ball on 2017-06-19
Welcome. You have no operating system installed. Help us help you. What exactly are you trying to achieve? Please give as much detail as possible. Are you trying to install Ubuntu?

You don't have grub installed, so SuperGrub is no use. Boot Repair probably a better option, but much use at the moment.

---

### Post by vimorcillo on 2017-06-19
Sorry. I want to install Ubuntu. I dont know what kind of information do you need, ask me and I give you everything you need. It´s the first time I have a problem with the grub like this error.

---

### Post by yancek on 2017-06-19
You don't have a problem with Grub other than the fact that it doesn't exist on your drive.  Your drive appears to have no OS on it so using the Ersse Disk and install should work and overwrite whatever might be on it, if anything if you select to format.  If you want more control, select the Something Else option which is a manual install.

---

### Post by efflandt on 2017-06-20
Your 500 GB drive appears to have 1 primary partition (/dev/sda1) that is probably not even formatted, since it has no UUID, and an extended partition (/dev/sda2) that is empty (no logical partitions in it). So unless you previously had something on that drive that you are attempting to recover, you could simply install Ubuntu using the entire drive ("Ersse Disk and install" mentioned should be "Erase Disk and install").

---

### Post by vimorcillo on 2017-06-21
Thanks for all. I used Blancco Drive Eraser and now my pc have Ubuntu fuctional.

---

