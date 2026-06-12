---
title: "Gnome fails on PXE boot"
date: 2007-06-28
forum: General Help
---

### Post by Mark Galeck on 2007-06-28
Hello,  

I am trying to setup a diskless PXE boot of Ubuntu desktop 7.04.  I read and followed available documentation and I think I am doing pretty well - I am booting, using the remote filesystem, the boot is proceeeding until various modules are starting, displaying OK message, until...

...Gnome tries to start, and hangs for a long time without "OK" and then I get 

/etc/init.d/rc:  2:  sed:  Input/output error

repeated many times, and nothing more.  


Anybody knows what the problem could be?  Thank you!

Mark Galeck

---

### Post by p.elsie on 2007-10-24
I am glad to find a post where someone else has encountered this problem.  I am encountering the same symptom on two attempts using the bootless procedures posted on ubuntu.com/community

I have however successfully done pxe diskless before (and still working).  One differences between my working cases is that they are Xubuntu whereas the cases that do not work are Kubuntu.  

I hope that helps some persons and perhaps helps someone to suggest a workaround for the Kubuntu installations.

---

### Post by p.elsie on 2007-10-26
You can probably disregard my first post as not-helpful.  As I recall now, my first success with a pxe boot used Kubuntu 6.06.  Xubuntu 7.04 is my current pxe boot and I now have the same set of files working for three different PC's (all with nvidia graphics) by simply swapping the xorg.conf.  

Kubuntu 7.10 is what I am playing with now.  My desktop installation used a laptop hard-disk (since it is temporary anyway until I copy the files to NFS) and I suspect that might have something to do with it.  Some one sent me this URL yesterday - [http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear](http://www.linux-hero.com/rant/explanation-ubuntu-hard-drive-wear-and-tear) - and after reading it I tried the command "hdparm -B /dev/hda" on my laptop and it returns what appears to be a normal response message.  The article does not address the question as to whether this problem affects desktops, so I tried "hdparm -B /dev/sda" on my server/desktop and it returned the same message followed by an error "Input/output error".  So I wonder if maybe /etc/init.d/rc script has some command in it that is only appropriate for laptops (or laptop HDD).

---

