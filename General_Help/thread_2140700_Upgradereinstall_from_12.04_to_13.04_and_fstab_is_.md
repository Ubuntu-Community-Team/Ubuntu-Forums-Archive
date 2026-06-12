---
title: "Upgrade/reinstall from 12.04 to 13.04 and fstab is not working anymore"
date: 2013-04-30
forum: General Help
---

### Post by Jimboland on 2013-04-30
In Ubuntu 12.04, fstab was working perfect with:

[B]192.168.10.104:/mnt/HD/HD_a2 /home/jimmy/nas nfs rw,hard,intr 0 0

[/B]In 13.04 its not working anymore, can somebody tell me, what/why (something) is changed in 13.04?:confused::confused:
It doesn't work at startup, and I can't mount it as root either. And there is no usefull information in syslog.

---

### Post by Jimboland on 2013-05-01
I found my problem. I had to install **nfs-common** before I could mount nfs shares again ](*,)
Thanks for your help guys :)

---

