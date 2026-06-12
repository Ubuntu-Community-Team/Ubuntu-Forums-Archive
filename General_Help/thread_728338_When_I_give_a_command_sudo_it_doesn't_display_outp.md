---
title: "When I give a command sudo it doesn't display output!"
date: 2008-03-18
forum: General Help
---

### Post by xelapond on 2008-03-18
Hello, 

This just started happening now(I have never had this problem before), whenever I run a command as sudo it does not display output, for instance:

```
alex@Andromeda:~$ aptitude search scite
i   scite                                                  - Lightweight GTK-based Programming Editor
alex@Andromeda:~$ sudo aptitude search scite
alex@Andromeda:~$
```

It does not even pause at all.

Any ideas how I can get sudo to work again?

Thanks, 

Alex

---

### Post by taurus on 2008-03-18
What's the output of this command?

```
id
```

---

### Post by xelapond on 2008-03-18
I just found more problems, Frets on Fire won't run, it just bounces the icon(I use KDE4) and then stops.  Also, when I try and play a song in Amarok is goes through every song like its done playing it, and never plays it, until it gets to the end of the list, then it says playlist finished.

---

### Post by xelapond on 2008-03-18
The output of id is:
```
uid=1000(alex) gid=1000(alex) groups=1000(alex)
```

Thanks for your help, this is the first time Linux has gone weird on me:^)

Alex

---

### Post by taurus on 2008-03-18
Looks like you have removed yourself, alex, from group admin in /etc/group.  Therefore, sudo doesn't work anymore.  

You need to boot into recovery mode from GRUB menu and add yourself back to group admin again.

```
adduser alex admin
shutdown -r now
```

---

### Post by xelapond on 2008-03-18
Thanks, I can now use sudo!

There are still a few problems though.  My music still will not play, and frets on fire will not open.  Are these related at all?  When I try and play a song it says:

> Audio output unavailable; the device is busy.
xine parameters

Thanks, 

Alex

---

### Post by taurus on 2008-03-18
You probably need to add your username, alex, back into a bunch of groups in /etc/group:  adm, audio, cdrom, video, plugdev, lpadmin, & games.

Don't forget to reboot.

---

### Post by xelapond on 2008-03-18
OK, I added myself to all of those that did not have something already.  cdrom(and a few others) has haldeamon already on there, what should I about those?

Thanks, 

Alex

---

