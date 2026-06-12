---
title: "mount a smb share after wifi is up?"
date: 2008-04-20
forum: General Help
---

### Post by mfaust731 on 2008-04-20
I want to automatically mount a samba share, but it is only available after wifi is loaded.
I tried putting it into fstab but it appartently tries to mount to early and fails.

after a wifi connection is made I can run " sudo mount //192.168.1.3/netshare /home/erin/server -o username=erin,password=mypassword" and it works just fine

what the best way to do this automatically?

---

