---
title: "Xserver fatal error"
date: 2006-09-09
forum: General Help
---

### Post by Kagrenak on 2006-09-09
This is the error I'm getting.

(EE) No devices detected. Fatal server error: no screens found

Nvidia 7600GT,
AMD 3200+
1002MiB of RAM
76GiB SATA 1.5 HDD

Wiki tells me to read /var/log/Xorg.0.log

Shell tells me I don't have permission to access it.

Any ideas?

Thanks.

Reposted from 6.06 forum, as I accedentally posted it there, but then realized I was using 5.10.

I just saw a hardware support subforum, I am not reposting it, again. I'll wait for someone to move it.

Update: Installed Nvidia default Drivers, now just black screen shows up after booting.

---

### Post by mssever on 2006-09-10
If the shell complains that you can't read something because of permissions, try using sudo. For example: 
```
sudo less /var/log/Xorg.0.log
```

---

