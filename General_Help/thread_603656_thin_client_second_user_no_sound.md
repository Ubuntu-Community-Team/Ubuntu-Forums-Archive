---
title: "thin client second user no sound"
date: 2007-11-05
forum: General Help
---

### Post by linuxboy123 on 2007-11-05
I am experiencing an anomaly with edubuntu and sound.

Edubuntu 7.10 with edubuntu-desktop-kde added.

symptoms  on a thin client using the first user created during install the sound works for both gnome and kde but the using the second user I created to match first user, sound works for gnome but not kde.   

I have seen threads out there referencing the order in which the user logins to the thin client.  I have tested that and this is not that issue.  I have rebooted the thin client and logged in initially with the second user and the symptoms remain.  First user gets sound no matter what order it is logged in which.

Any ideas where to start?

Thanks
linuxboy123

---

### Post by bingoUV on 2007-11-05
can you post the output of the following command after various kinds of login (first user, second user, gnome, kde)
```

ls -l /dev/dsp* /dev/audio* /dev/snd*

```

---

### Post by linuxboy123 on 2007-11-07
BingoUV,

the result of the ls commands were identical for all users.

I believe the issue is connected with the fact the first user is created during installation and the other not.  

I have changed the uid of the first user and no matter what I do to that first user, it still works.

I even joined the second user to the first users group and the second user still does not have sound.

---

