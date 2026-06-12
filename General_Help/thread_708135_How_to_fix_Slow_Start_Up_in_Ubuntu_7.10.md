---
title: "How to fix Slow Start Up in Ubuntu 7.10"
date: 2008-02-26
forum: General Help
---

### Post by cr8urf8 on 2008-02-26
This may come to help as some people. I had the problem where after the splash screen where the Ubuntu image comes up and you see the scrolling bar you it begins to load GNOME. It never reached the login screen for me. It would seat there as the screen changed colors. If this sounds like a problem you may be having read this.

First thing I did was I changed the "usplash.conf" That is located in "/etc/usplash.conf" Since I could not get into Ubuntu at all I booted off the live cd to get into the system to view my hard drive. I opened up the terminal set a root password by "sudo passwd" Made a password switched to the user root by "su root" entered the password I just created. After doing that I navigated to the file. For me it was "/media/disk1/etc/usplash.conf" Opened it up with nano. Then filled in "xres = 1024" "yres=768". After doing that I restarted the system. It allowed me to get to the login screen. I did system updates after restarting I noticed it would not allow me to get into the system again. I eventually figured it out. After GRUB begins to load Ubuntu and you see the splash screen press "ALT+F2" (F2 = Function Key 2) After doing that you should see text telling you what is loading up. After doing this it allowed me to access the login screen. I hope this helps any one having the same problems as me. :)

---

