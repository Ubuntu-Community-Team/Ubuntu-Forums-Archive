---
title: "Permission of files copied from CD/DVD are set to root"
date: 2008-05-29
forum: General Help
---

### Post by areteichi on 2008-05-29
Hi,
I'm currently using Hardy and I just realized today when I was copying some stuff from my data DVD to HDD using nautilus that the files copied onto HDD from the DVD had the permission set to root. I checked a couple other discs to make sure it wasn't just about the problem in the way I burned the DVD and found out that they all demonstrate this same problem. So right now, every time I copy something from a disc I would have to use sudo to set the permission back to me, and this is quite annoying. I don't know if this is the problem of Hardy or for some other reason, but I hope someone can help me out.

---

### Post by vishzilla on 2008-05-29
In the terminal type ```
sudo chown username /path/to/dir
```

---

### Post by areteichi on 2008-05-29
Sorry I wasn't clear.
What I would like to know is how I can set the system whenever I copy the files from CD/DVD so that the permission of files will be set to me as an user and not as root. This must be possible since that was the way ubuntu had been working me since Dapper.

---

### Post by vishzilla on 2008-05-29
I tried copying some files from a DVD. The permissions are set to me not root. :confused:

---

### Post by areteichi on 2008-05-29
> **vishzilla said:**
> I tried copying some files from a DVD. The permissions are set to me not root. :confused:

That's my point. That's how it is supposed to work but for some reason, my system is not doing that. I would like to know why and how I can fix this problem.

---

### Post by mc4man on 2008-05-29
Just to double check something. There's a 'regression' in hardy (though maybe it's a 'new security feature') where when you copy files and or folders from media mounted as read only that you only get read permission for files and access permission for folders. (will show little _lock icon_). It's a permissions issue and ownership is still with user, though you have to change the permissions to modify, create in or delete.
here's a thread about if that's your problem (no resolution atm, any suggestions welcome) [http://ubuntuforums.org/showthread.php?t=801528](http://ubuntuforums.org/showthread.php?t=801528)

So when you r. click, properties, permissions it says owner is root?

---

### Post by areteichi on 2008-05-30
You're actually right; the permission is just read-only and not set to root. Yeah I was just assuming when I saw that I was not able to write/modify the files that they belonged to root.

So I guess this is the problem of Hardy and there isn't a way to fix this yet?

---

