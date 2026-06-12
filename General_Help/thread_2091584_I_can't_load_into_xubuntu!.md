---
title: "I can't load into xubuntu?!"
date: 2012-12-05
forum: General Help
---

### Post by pavelexpertov on 2012-12-05
I got windows xp and xubuntu 12.10, which are installed alongside on the harddrive and it uses the usual boot manager (GRUB) so I can choose which one to use. Then, I ran out of space disk in xubuntu and I believe that I literally have zero space. but after turning on computer again, xubuntu could not load and it gave a black screen saying 'checking battery state' and it lasted like forever. Now I got stuck and I have no idea how to fix the problem. But i can still access windows xp though.

---

### Post by 2F4U on 2012-12-05
Have you resolved your space problem? If not, do you remember which partition ran out of space? Without any space left on the root or boot device, Xubuntu is most likely not able to boot. The first place to look if you can regain some space would be the folder /var/log, since it wouldn't cause any disturbance if you would delete log files. You could do this from Windows or from a Ubuntu liveCD.

---

