---
title: "Hardy freezes all the time"
date: 2008-06-14
forum: General Help
---

### Post by rikk on 2008-06-14
since today's ( June 13th ) Hardy system updates my desktop freezes every 3-5 minutes, in Firefox, Amarok and basically any application.
This is unworkable.
I had this problem before when upgrading from Gutsy to Hardy. After the system updates of the previous weeks the problem disappeared, now it's back again, 10 times worse !!

any help/suggestion ?

thx

---

### Post by prshah on 2008-06-14
> **rikk said:**
> since today's ( June 13th ) Hardy system updates my desktop freezes every 3-5 minutes, in Firefox, Amarok and basically any application.


Can you manage to post the output for the following command:```
cat /var/log/messages | tail -50
```

If you can't get your system to stay up long enough, maybe you should try booting off the live CD. Note that if you boot off the live CD, you will have to manually mount your linux partition to a mount location, eg "/mnt". In this case the command changes to ```
cat [color=red]/mnt[/color]/var/log/messages | tail -50
```

You should also check if the live CD stays alive for 15 mins or more without freezes. This will help eliminate system causes (temperature, bad ram, hdd bad sectors, etc).

---

