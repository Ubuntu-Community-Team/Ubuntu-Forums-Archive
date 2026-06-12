---
title: "Mounting My NAS"
date: 2007-11-18
forum: General Help
---

### Post by Mongo5000 on 2007-11-18
Sorry, couldn't really understand anything from the other posts I found.  Found[ this one]("http://ubuntuforums.org/showthread.php?t=212151") and it got me this far.

I can mount it with fstab by running 

```
sudo mount -a
```

But upon reboot, it wont connect since the mount -a asks for a password.  My NAS doesnt require authentication so not sure how to change my fstab to use no password.

Here is the line from my fstab
```
//192.168.1.104/PUBLIC	/home/stephen/Desktop/mybook smbfs	defaults  0  0
```

How do I change it so it mounts automatically on boot and not require a password?

---

### Post by Craigus on 2007-11-18
This may be relevant:

[http://ubuntuforums.org/archive/index.php/t-484126.html]("http://ubuntuforums.org/archive/index.php/t-484126.html")

> smbfs is unmaintained and known to be severely broken

doesn't sound very encouraging. My FreeNAS box provides NFS, so I haven't had this issue.

---

### Post by Mongo5000 on 2007-11-18
weird, seems that the same mount point doesn't work now.  ubuntu just locks up and becomes unresponsive for a bit.

Any other options I have rather than using smbfs?  I do need it available to my apps so Connect To Server won't work.

---

### Post by Craigus on 2007-11-18
Have a look here:

[http://joey.ubuntu-rocks.org/blog/2007/04/25/resolution-to-mounting-samba-shares-dont-use-smbfs/]("http://joey.ubuntu-rocks.org/blog/2007/04/25/resolution-to-mounting-samba-shares-dont-use-smbfs/")

---

### Post by Craigus on 2007-11-18
And, sorry, here:

[http://ubuntuforums.org/showthread.php?t=288534]("http://ubuntuforums.org/showthread.php?t=288534")

---

### Post by Mongo5000 on 2007-11-18
Just to confim then, I would want to use fusesmb rather than cifs since I don't require authentication.

Do I have that right?

---

### Post by Craigus on 2007-11-18
From the second link I posted:

> If your samba share does not require a password (shame on you  ) just use the following line instead:


sudo mount -t cifs //netbiosname/sharename /media/sharename -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777



---

### Post by Mongo5000 on 2007-11-19
> **Craigus said:**
> From the second link I posted:

That works, but don't have write access.  Read only

---

### Post by Mongo5000 on 2007-11-19
so what does work is when I change the mount point to a folder under my home directory instead of my /media directory.

Why is that?

EDIT: i only have write access to the main directory.  Any sub directories, no write access
EDIT 2: Well, temporary solution I came up with is that I have it mounted twice.

If I use the Connect to Server way, I get full read/write access.  I also have it mounted with read only to a directory in my home folder allowing my apps to use it.  This was frustrating.

---

### Post by Craigus on 2007-11-19
It's not simply the > dir_mode=0777

is it? That seemed to not have copied correctly in my post above ...

---

### Post by Mongo5000 on 2007-11-19
> **Craigus said:**
> It's not simply the 

is it? That seemed to not have copied correctly in my post above ...

hehe, no, I just figured it was  a typo :)

---

