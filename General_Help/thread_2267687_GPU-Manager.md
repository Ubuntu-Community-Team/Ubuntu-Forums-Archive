---
title: "GPU-Manager"
date: 2015-03-03
forum: General Help
---

### Post by brian51 on 2015-03-03
I was messing around with my gpu-manager working to get my nvidia card to work correctly. In the process I accidentally deleted the gpu-manager script. So, I was wondering if anyone could provide the default script so I can retype it in there.

---

### Post by dino99 on 2015-03-03
here is what i have inside /etc/init/gpu-manager.conf

start on (starting lightdm
          or starting gdm
          or starting kdm
          or starting xdm
          or starting lxdm)
task
exec gpu-manager --log /var/log/gpu-manager.log

---

### Post by Yellow Pasque on 2015-03-03
Just reinstall the package:
```
sudo apt-get install --reinstall ubuntu-drivers-common
```

---

