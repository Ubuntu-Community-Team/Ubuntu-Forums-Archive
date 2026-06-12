---
title: "Accessing files on Ubuntu server"
date: 2005-10-28
forum: General Help
---

### Post by Wrosmo on 2005-10-28
I have a problem. I have a server where all my music, movies and pictures is stored. And I have a laptop. The server runs Ubuntu Hoary and the laptop has dualboot with winXP home and Ubuntu Breezy. 

In winXP I can connect to the server via samba and open files (listen to music, view videos and pictures), but with Ubuntu I have to copy the files to the local harddrive before I can open them (via samba). 

I think this is hopeless, how can winXP communicate better with my linux server than linux can itself?

How can I get rid of this problem? Can I mount a folder on the server onto the laptop in any way?

---

### Post by z_pod on 2005-10-28
Hi,

I'd suggest you to try assign a moutpoint to the smb share the same way you'd do with NFS shares.

Regards

---

### Post by Wrosmo on 2005-10-28
Could you show me how to mount a sambashare. I have tried following instruction on several sites, but I cannot get the sambashare to mount.

---

### Post by ipn1nj4 on 2005-10-28
mount -t smbfs -o username=tridge,password=foobar //fjall/test /data/test

That is how I do it

---

### Post by Mr. Electric Wizard on 2005-10-28
First off, on the Ubuntu Server have you shared the folders (music, pictures, etc.)?
You cand do this through system-->shared folders I believe.
Then on your laptop you will need to edit the fstab (for share avalailability at startup), to mount the share.
This Thread helped me a lot:
[http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+fstab]("http://www.ubuntuforums.org/showthread.php?t=26438&highlight=samba+fstab")

Good luck.:)

---

### Post by Wrosmo on 2005-10-28
Now it workes!

The problem was that I didn't know I had to install the smbfs package.

Thank you!

---

