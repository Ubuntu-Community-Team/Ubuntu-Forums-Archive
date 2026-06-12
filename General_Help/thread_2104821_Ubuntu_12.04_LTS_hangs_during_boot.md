---
title: "Ubuntu 12.04 LTS hangs during boot"
date: 2013-01-14
forum: General Help
---

### Post by Default112 on 2013-01-14
Hi,

I have a DELL PowerEdge R510 running Ubuntu 12.04 LTS Server. This Server has a PERC H700 Raid Controller which I configured to a single RAID5 volume. Installation went well without any errors. Everything is installed onto lvm volumes. I have 3 of them. The root volume, the home volume and a volume for various data. 
The last thing I did was installation and configuration of samba, ldap and quota (for the home volume). After that I had to shut down the server and relocated it to another server cabinet. Now it hangs during boot. Blank screen after grub. I removed the gfx mode from the boot entry and got the output. Now it hangs with this output:
 [[IMG]http://i638.photobucket.com/albums/uu109/default112/th_IMG_0440_zps64769975.jpg[/IMG]]("http://s638.beta.photobucket.com/user/default112/media/IMG_0440_zps64769975.jpg.html")

Any suggestions? 

Default112

Edit: I tried booting from Ubuntu live dvd. Works like a charm and I can access all volumes...

---

