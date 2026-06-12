---
title: "Change read/write permsission from terminal"
date: 2006-10-23
forum: General Help
---

### Post by rocknrolf77 on 2006-10-23
Installed parallels workstation and it changed my read/write persmission for my Home/.dmrc  file. How can I change the permission to it's original state from a terminal? When i try to log in from GDM it says that the file should have the file-permission "644" The $Home.directory most be owned by user and not writable for other users. ](*,)

---

### Post by CatKiller on 2006-10-23
```
chmod 644 .dmrc
``` I think. **man chmod** will tell you more.

---

### Post by lloyd_b on 2006-10-23
Another person had the same problem.  We changed the permissions on that file.  We checked the permissions on the parent directory.  Nothing helped.

Final solution - delete the file.  It will be automagically recreated the next time you boot (you can save a copy of it if you want).

Note: you'll probably have to "sudo rm .dmrc" - in the previous case, the user couldn't delete the file (even though it showed that user as the owner!).

Lloyd B.

---

### Post by taurus on 2006-10-23
Actually, root has the ownership of that file.  That's why the user can't write to it and therefore can't start Gnome!!!  However, the user should own it but somehow the ownership got changed...

---

### Post by rocknrolf77 on 2006-10-23
Managed to chmod my /home and / directory too, easy to idiotic things when you are frustrated over something. Is there a way to set these folders back to default or something? Just get the message  can not cd to home.

---

### Post by bsussman on 2006-10-23
/ should be 755 owned by root/root
/home 775, same ownership

just use sudo chmod from anywhere, then test cding to them.

---

### Post by rocknrolf77 on 2006-10-23
> **bsussman said:**
> / should be 755 owned by root/root
/home 775, same ownership

just use sudo chmod from anywhere, then test cding to them.


Can I do this from rescue mode? Just wondered since I can noot log in.

---

### Post by bsussman on 2006-10-23
Yes you can - you just need to find the correct directory tree - I do not remember where rescue mode mounts your existing volumes.

---

### Post by taurus on 2006-10-23
> **bsussman said:**
> Yes you can - you just need to find the correct directory tree - I do not remember where rescue mode mounts your existing volumes.
It mounts everything according to /etc/fstab.  However, it will drop you into a shell with root access so be careful.  Assuming you use john as your login name, then change your $HOME directory as

```

chown -R john:john /home/john

```
And if you run "ls -la /home", you should see /home/john is owned by john and group john as well...

---

### Post by rocknrolf77 on 2006-10-23
Didn't get it working so I just started X as root and took backup. Did a fresh edgy install instead. But thank's for the help anyways. :)

---

