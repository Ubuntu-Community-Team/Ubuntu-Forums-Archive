---
title: "Samba connection problems"
date: 2006-12-11
forum: General Help
---

### Post by Elijah on 2006-12-11
I used the addsamba script to generate connection to our shares. This works on all our workstations using dapper, but recently I upgraded to edgy and started to experience these problems. 

All my shares times out, I can't 'ls' from it's own mounted directory and gnome won't also boot properly because it waits for it to mount. I have to unmount(umount -f) it and remount(mount -a) it for it to work. 

I don't see any problem with my fstab samba mount: 
```
# Added by the addsamba utulity
 \\devserver\htdocs /media/samba/devserver/htdocs smbfs auto,fmask=0666,dmask=0777,credentials=/etc/samba/passwords/devserver-htdocs
# Added by the addsamba utulity
 \\devserver\share /media/samba/devserver/share smbfs auto,fmask=0666,dmask=0777,credentials=/etc/samba/passwords/devserver-share

```

Are there any known bugs on smbfs or something I didn't know about? or something else is causing this connection problem?

---

### Post by scrooge_74 on 2006-12-11
should had stayed with 6.06 and waited to have all bugs taken care off

---

### Post by Elijah on 2006-12-11
so there is a bug?

---

### Post by Elijah on 2006-12-12
*BUMP* 

found a clue, I have 3 shares and when I comment out 1 everything works again by bootup. It's this particular share that gets me this 'device busy' whenever I tried to unmount it. 

Any idea how to work through this?

---

### Post by Phlosten on 2006-12-17
I just started to run into issues mounting samba shares on boot. I just figured out however that when my system is booting it is mounting the fstab entries before the network is brought up. Not sure if this is related to the additions to the boot process as it moves to upstart.

I my particular case samba is basically getting stuck and I even have HAL crashing on start, plus a samba error on restart. Once I comment out my single samba share mount all those problems disappear.

I was just about to look into setting up a boot script to do the mounting further on down the line, but thought I would do some searching on the problem. Chrisfay has posted an init script here [http://www.ubuntuforums.org/showthread.php?t=318433](http://www.ubuntuforums.org/showthread.php?t=318433) which should do the job.

Does anyone know how to go about forcing the system to bring the network up earlier before the file system mounting? or is this not possible?

---

