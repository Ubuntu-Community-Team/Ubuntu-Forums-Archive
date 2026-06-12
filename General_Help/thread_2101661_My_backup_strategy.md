---
title: "My backup strategy"
date: 2013-01-05
forum: General Help
---

### Post by mkander on 2013-01-05
I have been working to find an optimal bare metal backup strategy and would like som input on my current setup.

I have one big root partition where ubuntu and everything is installed. What I do now is as follows:
1) Flush mysql databases and lock all tables.
2) Create a lvm snapshot and mount it
3) Unlock mysql
3) tar everything on the lvm snapshot and store on a NAS
4) dd the lvm snapshot partition to an image file and store it on a the NAS
5) Unmount and erase the lvm snapshot

What I have running on the machine is apache, mysql, ftp, samba and some small programs.

Is this sufficient if the disk fails and I need to do a complete restore? I then plan on inserting a new disk, boot up and dd the image file to the new disk. Will everything be up again then? Or do I have to do something in fdisk and grub or anything?

Any input would be great ;)

---

