---
title: "ghost?"
date: 2008-04-07
forum: General Help
---

### Post by evilbuntu on 2008-04-07
hi everyone

i was looing into ghost 10 for a project i want to do. I want to build an xp proxy and back up server for my basement on an old hp vectra i have. the question is will ghost 10 backup my linux ubuntu partition and files okay on an xp machine?????

if not can someone telll me a decent software that might, i have seen posts on trueimage (?) but i cant tell if that is a LINUX only software.

thanks in advance........

---

### Post by MrFSL on 2008-04-08
Yes Ghost can backup a ext3 partiton.

However there are other free choices that might be smarter. For full disk imaging I would suggest PartImage. [http://www.partimage.org/Main_Page](http://www.partimage.org/Main_Page)
This can be installed from the repos.

But, In terms of backups, full disk backups take a lot of space and aren't usually very practical. I suggest using rsync. (also in the repos) to do differential backups.
[http://en.wikipedia.org/wiki/Differential_backup](http://en.wikipedia.org/wiki/Differential_backup)

---

### Post by noynac on 2008-04-08
> **evilbuntu said:**
> ...if not can someone telll me a decent software that might, i have seen posts on trueimage (?) but i cant tell if that is a LINUX only software.

Acronis (which owns the True Image software) has an imaging product for Linux, but it's intended for business use and the cost is prohibitive. I Use True Image Home to image my dual-boot WinXP/Ubuntu machine, and it works fine. You could also use True Image Home to backup a Linux-only computer, but you would have to boot to the True Image CD to create or restore the image. The downloadable version of True Image Home can be gotten from NewEgg for about $25.00.

BTW, Seagate/Maxtor gives away an OEM version of True Image 10 for users of their drives. You have to have a Seagate or Maxtor drive in your system, but that's the only difference. I haven't used it, but it can be downloaded from:

[http://www.seagate.com/www/en-us/support/downloads/discwizard/](http://www.seagate.com/www/en-us/support/downloads/discwizard/)

---

### Post by ramjet_1953 on 2008-04-08
The Gparted + CloneZilla Live CD will do what you want admirably.

It is Open Source and CloneZilla clones a disk much faster than Ghost for Linux, as it only copies the used section of the source drive.

Here's a link: [http://gpartedclonz.tuxfamily.org](http://gpartedclonz.tuxfamily.org)

Regards,
Roger :cool:

---

### Post by evilbuntu on 2008-04-08
Guys thanks so much
the reason I am interested in ghost is due to a job I am starting
I will probably not be. Doing a system backup 
anymore but still a file backup and xp proxy
since ghost will do this I guess I will be good
I will prob just do a clone of my laptops xp for practice
i will be sure to thank you guys when I'm not doing this from my iphone

Also guys I'm refering to ghost for xp not a Linux specific version, will ghost for windows be able to read the folders I wish to back up from my ubuntu machine as long as they are samba shared?

---

