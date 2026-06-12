---
title: "Linux 2.6.11.11 and nvidia's 1.0.7664 drivers"
date: 2005-06-09
forum: General Help
---

### Post by endy on 2005-06-09
Hi, I rolled my own kernel and installed nvidia's drivers off their site and everything is great until I reboot.

After reboot '/usr/lib/tls/libnvidia-tls.so.1.0.7664' and '/usr/lib/tls/libnvidia-tls.so.1' have been deleted and I have to reinstall the nvidia drivers again. 

Does anyone know why ubuntu is deleting these files? How can I stop it?

Thanks

---

### Post by skoal on 2005-06-09
Don't start "nvidia-glx" in your runlevel.

\\//_

---

### Post by endy on 2005-06-09
I just now took the executable permissions from the '/etc/init.d/nvidia-glx' file and it works.

Thanks.

---

