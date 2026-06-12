---
title: "Trouble Updating procps"
date: 2013-10-30
forum: General Help
---

### Post by jrolland2 on 2013-10-30
Hello, all!

I am running Unbuntu 12.04 Precise Pangolin LTS Desktop version on an Acer Aspire system.

I am having trouble trying to update procps on my system. It just got to the point that, as I was trying to use Update Manager to do a few routine updates, my system tried to update my distro version, so I had to quickly power it down and restart. It restarted with a file lock on dpkg - after several clean shutdowns and reboots - so I have to kill/remove the file lock on dpkg. Now, it only shows procps as needing to be updated (which, there were 43 updates to be installed before this fiasco a half hour ago) and won't update procps.

If anyone can offer any assistance as to how to properly update procps, I would be most appreciative and would provide any needed additional system info.

Thanks much in advance for any assistance you can provide.

---

### Post by deadflowr on 2013-10-30
What happens if you run
```
sudo dpkg --configure -a
```

---

