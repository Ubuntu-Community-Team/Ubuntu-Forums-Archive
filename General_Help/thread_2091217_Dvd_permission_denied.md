---
title: "Dvd permission denied"
date: 2012-12-04
forum: General Help
---

### Post by Amusingdock25 on 2012-12-04
Hi, this is probably going to be a noob question, but I'm not that experienced with...well stuff. Anyhow I was using playonlinux to install HL2, but when I came to the screen where I was supposed to enter my dvd path I got confused. When I typed the path in it said permission denied... So yeah if anyone can tell me how to change permission to the read only disc that would be great. Oh and I tried sudo chmod +x but it did nothing. And btw, my path says /media/august/QUAKE4 cause of my previous installation of Q4 but even tho I mount HL2 it still says QUAKE4. Sorry for all the noob questions and thanks in advance.

---

### Post by trogdor1138 on 2012-12-05
Take a look at the documentation for mounting: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

You can only mount an optical drive's file system as read-only. You also can't set the permissions bits for a CD or DVD, but you don't need to do that anyway.

As an aside, +x sets the executable bit for files and directories. For files, this allows them to be run by a shell (ie BASH). For directories, it allows you to traverse them. Like I said, you can't modify this, but if anything you would need to execute 'chmod +r' to gain read access.

You probably are looking for something like:

```
sudo mkdir /mnt/HL2
sudo mount /dev/cd /mnt/HL2
```

Ubuntu should normally auto-mount optical drives I believe, but the above should get you on the right track if not.

---

