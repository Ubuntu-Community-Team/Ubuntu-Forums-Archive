---
title: "Can I share my cdrom drive"
date: 2008-05-10
forum: General Help
---

### Post by Ripfox on 2008-05-10
with my xbox? :)

I am experimenting and got this 

> 'net usershare' returned error 255: net usershare add: cannot share path /media/cdrom0 as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.

---

### Post by Ripfox on 2008-05-10
bump

---

### Post by Ripfox on 2008-05-11
bumpppaa:)

---

### Post by damis648 on 2008-05-11
Either take ownership of /media/cdrom and try again or
```
sudo gedit /etc/samba/smb.conf
```
and find [global] and add that option.

---

### Post by Ripfox on 2008-05-11
I figured that was the next step, but really my question was has anyone ever done this and will it work...I mean controlling my DVD drive remotely. :)

---

### Post by damis648 on 2008-05-11
Well you wouldnt be controlling it, you would be just viewing the files in it.

---

### Post by Ripfox on 2008-05-11
Well, in a way, b/c I have XBMC installed on my xbox (softmod) and I would be potentially "initializing" it to spin and consequently feed the data on the disk to the xbox...:)

---

