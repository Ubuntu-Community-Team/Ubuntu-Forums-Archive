---
title: "Howto disable all Cron job autorun"
date: 2020-08-17
forum: General Help
---

### Post by aboka on 2020-08-17
hi, im running Ubuntu 20.04 on a vps and i like to disable a program's cronjob. I hv delete anything relate to it inside '/etc/crontab/' and '/etc/cron.*/*', but i cant seems to disable it inside 'systemctl timer'. I could list them with 'systemctl list-timers' and it will show -

```

Tue 2020-08-18 04:31:18 +08 12h left      Mon 2020-08-17 12:23:01 +08 3h 9min ago  certbot.timer                certbot.service

```

i tried this command -
```

sudo systemctl --user disable certbot.timer
sudo systemctl --user disable certbot.service

```

but i will get error - 'Failed to connect to bus: No such file or directory'

p/s - root is disabled, and i login and use another account with sudo for this

thank you,

---

### Post by dino99 on 2020-08-17
Why disabling certbot ?

related topic: [https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04)

---

### Post by aboka on 2020-08-17
hmmm, i think i hv solve this with -

```

sudo systemctl stop certbot.timer
sudo systemctl disable certbot.timer

```

---

### Post by aboka on 2020-08-17
> **dino99 said:**
> Why disabling certbot ?

related topic: [https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-20-04)

hi, i like to do it manually instead of it running twice daily. thanks

---

