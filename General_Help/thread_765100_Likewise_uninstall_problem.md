---
title: "Likewise uninstall problem"
date: 2008-04-24
forum: General Help
---

### Post by Legend1222 on 2008-04-24
I wasn't able to reproduce this, so i'm not filing a bug report, but this did happen to me, so it will probably happen to someone else.

If your experimenting with Likewise, get frustrated with it (thats another story) and uninstall it, it might slap you in the face further by not completely uninstalling. 

If you try to login once likewise is uninstalled and get "Module Unknown" (not the exact wording) and you CAN'T login to your system anymore, reboot into Rescue mode and issue the command "find / -name *lwidentity*". It will come back with a bunch of files named *.lwidentity.original. 

You need to rename everyone of these files back to their original names to get you system to work right again. For example, to fix the hosts file, use the command "mv /etc/hosts.lwidentity.original /etc/hosts". Repeat for every file listed. 

Hopefully this helps someone. I saw similar, but not identical posts on other forums, and everyones solution was "reinstall". Thats not necessary.

---

### Post by gotee12 on 2008-04-28
Thanx a ton for this info! I tried out Likewise-open and didn't like how it set up some things for the domain accounts. 

Likewise-open pretty much left my system a mess when I uninstalled it.

---

### Post by doonavin on 2008-05-18
Had the same problem.  Just confirming that the workaround works incase anyone else has the problem.  Thanks a lot man!

---

### Post by JaxDomino on 2008-06-17
Thanks!  I will try this.  I tried to uninstall and I got Authentication failure after reboot.  I actually had to REINSTALL Likewise!  It's like a virus or spyware that won't go away!

---

### Post by joe.davis on 2008-07-11
I have setup likewise on two ubuntu boxes and removed it from both of them. 

I installed it on the first using apt-get and the ubuntu repositories. When I removed it from that box, I had the problem described above.

I installed it on the second box using the installer from likewise. When I removed it, everything worked just fine!

Could this be a problem with the distro in the ubuntu repository? Also the ubuntu distro does not include a lot of libs required for integration with samba.

---

### Post by Harold Parker on 2008-12-02
I wanted to install Likewise to use with samba. Never got it fully working. I did the install from the Ubuntu repository. Do you think I could do the Likewise install over what I currently have?

---

### Post by Zwulf on 2010-10-30
Nothing I tried or found somewhere worked to get this piece of crippled virus out of my system. Uninstall is not possible. Every time system tries to do so /etc/ssh/ssh_config.lwidentity.orig is created again, no way to get it out. Neither the solution described here works, nor reinstall (which is not possible because of the error, just crazy). PLEASE anyone? :confused:

I'm about going mad on this... I don't want to reinstall Ubuntu completely just to get away this extremely annoying error. :mad:

---

