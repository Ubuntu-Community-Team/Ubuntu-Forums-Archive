---
title: "hello,i need help plz"
date: 2013-03-27
forum: General Help
---

### Post by zombieze on 2013-03-27
hi,when i tries to install [COLOR=#ff0000]Ubuntu[/COLOR] on [COLOR=#ff0000]windows 8 pro-64bit[/COLOR] on separate partition he doesn't work, look at the video link
[https://www.youtube.com/watch?v=1zhpwqFKPyE&list=HL1364357389&feature=mh_lolz](https://www.youtube.com/watch?v=1zhpwqFKPyE&list=HL1364357389&feature=mh_lolz)

plz help

---

### Post by drmrgd on 2013-03-27
It looks like you're trying to do a Wubi install of Ubuntu with your Windows 8.  Looking around, it looks like at this time Wubi is not compatible with UEFI on GPT formatted disks, which is likely what you have there.  Here's a link with a similar problem and maybe some more info:

[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)
[http://askubuntu.com/questions/225048/is-wubi-for-windows-8](http://askubuntu.com/questions/225048/is-wubi-for-windows-8)

In order to run Windows and Ubuntu in this case, it looks like you may need to set up a full dual boot by repartitioning your hard drive to accommodate the Ubuntu OS, and setting up a full install of Ubuntu on the second partition.  Maybe more effort than you want?  If not, post back, though as there are quite a few folks here who are experts at setting such a system up with minimal effort.

---

