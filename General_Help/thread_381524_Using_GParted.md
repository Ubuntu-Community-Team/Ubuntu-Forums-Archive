---
title: "Using GParted"
date: 2007-03-11
forum: General Help
---

### Post by Buster95 on 2007-03-11
Downloaded Gparted to a temp file, unpacked it, burned it onto a disk.

Do I reboot to automatically invoke the Gparted program?
Or do I boot up Edgy and start the partitioner out of the CD?

Thanks

---

### Post by taurus on 2007-03-11
What exactly are you trying to do because you can install gparted in Ubuntu?

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by Buster95 on 2007-03-11
> **taurus said:**
> What exactly are you trying to do because you can install gparted in Ubuntu?

```
sudo aptitude update
sudo aptitude install gparted
```

Thanks Taurus,
I couldn't obtain gparted with sudo aptitude update because it doesn't work. That's why I tried the disk approach.
Here is a printout of that particular fault.

xx@laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) edgy Release.gpg                               
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                        
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
0% [Connecting to au.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubunt

That's not the whole printout. It goes on and on as it works through the modules, but I hope you get the picture.
Cheers

---

