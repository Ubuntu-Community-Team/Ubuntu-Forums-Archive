---
title: "Ipod not mounting after upgrade"
date: 2008-05-04
forum: General Help
---

### Post by Prozzy on 2008-05-04
Hey

So i just upgraded to 8.04 the other day and everything seemed to be working just fine, but now i just figured out when i wanted to update the music on my ipod that it didnt mount.

In 7.10 an icon would show up on my desktop but in 8.04 nothing shows up.

according to "fdisk -l" and "lsusb" the ipod is connected just seems like it isnt mounted. I dont remember if i edited the /etc/fstab in 7.04, i tried adding

/dev/sdb2 /media/ipod vfat nosuid,noauto,nodev,rw,umask=077,gid=1000,uid=1000,user,defaults,noatime,iocharset=utf8 0 0

to my /etc/fstab with no luck.

i got libgpod 1 and 3 installed


Any ideas on how to get the ipod mounted/working? In 7.10 i was using amaroK for transfering files and allready tried the auto-detecting.

Thanks

---

