---
title: "hdd not appearing"
date: 2008-06-29
forum: General Help
---

### Post by gary - irl on 2008-06-29
Hey guys -- I'm new to Ubuntu. Just installed it about an hour ago... Only real issue I'm having is that one of my hard drives is not appearing. I can't access the files. 

Is it because I installed Ubuntu on my C: drive (my main HDD)? The other drive im trying to access is a 250 gig Western Digital (G: drive).

I would think that maybe my other Hard drive isn't compatible, but both are WD, so I would guess not. 

I have all of my media files saved on this large hard drive so if I can't access them, I'll have to switch back to windows xp.

Any help would be appreciated. Thanks!

---

### Post by VMC on 2008-06-29
Open up a Terminal from "Application-Accessories-Terminal"
Then type in the following:

```
sudo fdisk -l
```

Post the output of that command. It will show all you hard drives attached to your computer.

---

