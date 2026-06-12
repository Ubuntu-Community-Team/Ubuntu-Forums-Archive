---
title: "help needed with hamachi"
date: 2007-12-12
forum: General Help
---

### Post by zzzPOOHzzz on 2007-12-12
i'm trying to set up hamachi to work, but it just isn't i don't know what's up with it.

it's not keeping any of my settings... it's not really doing anything haha...

it seems like its installed, but if i try to do something, it doesn't confirm it worked or tell me if something is wrong

---

### Post by handband2 on 2007-12-13
Try this howto:
[https://forums.hamachi.cc/viewtopic.php?t=16174&sid=07597a4374736d72520ea82cfa08bb7d](https://forums.hamachi.cc/viewtopic.php?t=16174&sid=07597a4374736d72520ea82cfa08bb7d)

---

### Post by zzzPOOHzzz on 2007-12-13
awesome this got me further into what i needed but now it just says "hamachi could not be started..."

---

### Post by zzzPOOHzzz on 2007-12-13
i think i got it... i ran
"sudo ghamachi" and now it's working awesome!
now just to figure out how to get starcraft working.... :)

---

### Post by handband2 on 2007-12-13
If you want to run ghamachi and/or hamachi-gui under your user account rather than sudo, change ownership of your files in ~/.hamachi.

The following command will do this:
```

sudo chown -R $USER:$USER ~/.hamachi

```

---

