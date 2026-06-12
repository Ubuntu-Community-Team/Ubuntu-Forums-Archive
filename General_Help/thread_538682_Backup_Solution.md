---
title: "Backup Solution?"
date: 2007-08-30
forum: General Help
---

### Post by breenmachine on 2007-08-30
Hi, Is there any Backup programs for Linux that will allow an image of the partition to be created while it is mounted?  I want to schedule automatic backups weekly to a server (FTP,NFS,whatever) but don't want to have to deal with booting into a live CD.

I'm not as concerned with my data as I am with just my installation and packages/programs I have installed and configured thats why I'm looking at images, it took me forever to get this installation setup the way I want it on my laptop with everything working.

Thanks.

---

### Post by FleetAdmiral74 on 2007-08-30
I didn't think any program could do a full image w/ a mounted disk. Otherwise I would suggest [http://orgs.man.ac.uk/documentation/partimage/index-3.html](http://orgs.man.ac.uk/documentation/partimage/index-3.html)

Nice program, images the whole partition.

edit: if you are mostly concerned with programs and settings...not data, probably a better way then this. Lets see what comes along...

---

### Post by indytim on 2007-08-30
Partimage.

But as FleetAdmiral74 mentioned, you can not do a backup image of your mounted ops partitiion.  There is a recovery disc that can be run from boot which has both GParted and Partimage on it.  That will allow you to boot to the CD and do your partition backups.  

I'm at work (on Win2k) so I don't have the url for the recovery CD.  Perhaps someone else can chime in with the url.

Indytim

---

### Post by breenmachine on 2007-08-31
Thanks for the replies.  I already have a copy of the CD I think you're talking about, and it does work well at what it does, I guess I'll have to stick with that, thanks.

---

### Post by Foxray on 2007-08-31
Not sure about a single image, but for backups while its mounted I'd use rsync or tarball. I usually put this line into the crontab and run it every week.

rsync -av <source directory> <destination directory>

careful with trailing slashes though they can be tricky.

---

