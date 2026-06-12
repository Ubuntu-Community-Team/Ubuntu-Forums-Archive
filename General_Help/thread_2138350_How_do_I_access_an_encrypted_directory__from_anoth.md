---
title: "How do I access an encrypted directory  from another computer?"
date: 2013-04-23
forum: General Help
---

### Post by kinikry on 2013-04-23
BACKGROUND: While the title may seem misleading, I am not cracking. So basically, I reinstalled Windows 7, destroying grub. I apparently failed at restoring grub, and left me frusterated. 
I took apart my computer, and I have used a sata-to-usb cable to hook up my desktop's hdd to my laptop. 
My goal is to take the important files off of the hard drive then reformat. 
PROBLEM: When  I attempt to acess the /home/USER/  file, all that is there is a .txt file which says 

[SIZE=3][COLOR=#000000]THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
[/COLOR][/SIZE]
This is presumbly because I used the "encrypt home directory" option when installing. I know the password, so is there any chance of me being able to get my data back?

---

### Post by papibe on 2013-04-23
Hi kinikry.

I would recommend taking a look at ecryptfs-recover-private. Here's a simple [tutorial]("http://blog.dustinkirkland.com/2011/04/introducing-ecryptfs-recover-private.html").

Regards.

---

### Post by Isamu715 on 2013-04-24
Have you tried following the suggestions in that text file (i.e. using the "Access Your Private Data" option in GUI or *  ecryptfs-mount-private* from the terminal)?

---

