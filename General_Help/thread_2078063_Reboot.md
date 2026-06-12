---
title: "Reboot"
date: 2012-10-30
forum: General Help
---

### Post by twinkle_stars on 2012-10-30
Hi,

I need to check who reboot the ubuntu server with the ip address, date and time



Thanks & Regards

Twinkle

---

### Post by kanikilu on 2012-11-02
The only thing close to that, that I know of, is the *last* command. Look for "reboot" in the output of that command. It won't show IP address, though.

If you have old versions of the wtmp log in /var/log (e.g. wtmp.1, etc.), use the -f option: ```
last -f /var/log/wtmp.1
```

Maybe someone else knows of something better...?

---

