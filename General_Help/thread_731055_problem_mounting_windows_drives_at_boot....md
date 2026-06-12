---
title: "problem mounting windows drives at boot..."
date: 2008-03-21
forum: General Help
---

### Post by Mia_tech on 2008-03-21
when I first installed ubuntu I was able to mount my windows remote drives without problem, now they are showing on my desktop but it's not responding and I change directory to that folder and nothing is in it...here is what I was using on my /etc/fstab

//x.x.x.x/share /media/share smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777 0 0

that stoped working so I switch to this

//10.200.50.7/winshare	/media/winshare  cifs	auto,credentials=/root/.smbcredentials,dir_mode=0777,file_mode=0777	0	0

that isn't working either...but I can access the remote file doing Places->Connect to Server
so the share is there
anybody know what could be wrong?

thanks

---

