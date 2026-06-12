---
title: "Can 8.04 RC be converted to final release..."
date: 2008-04-23
forum: General Help
---

### Post by Kincer on 2008-04-23
...or is it the same thing?

If so, would it just be a matter of apt-get update / apt-get upgrade or something different?

Thanks!

---

### Post by Tim Sharitt on 2008-04-23
If you already have the hardy beta or rc installed getting the final release should just be a simple update using update-manager or apt-get update.

---

### Post by Exsecrabilus on 2008-04-23
What will that be like?

Do bug fixes and new packages appear and the Update Manager notifies you when Ubuntu 8.04 is released?

---

### Post by noynac on 2008-04-23
> **Exsecrabilus said:**
> What will that be like?

Do bug fixes and new packages appear and the Update Manager notifies you when Ubuntu 8.04 is released?

It hasn't worked that way in the past. Just keep updating and you'll have Hardy final. In fact, if your install is current, you may have Hardy final right now.

---

### Post by Kincer on 2008-04-23
Where can you verify the current install (Hardy / Fiesty / Gutsy / etc)?

---

### Post by noynac on 2008-04-23
> **Kincer said:**
> Where can you verify the current install (Hardy / Fiesty / Gutsy / etc)?

It is shown by the system monitor tool.

system > administration > system monitor > system

---

### Post by Simpatico on 2008-04-23
If you prefer the command line:

```
cd /etc
cat issue
```

```
/etc$ cat issue
Ubuntu 8.04 \n \l
```

---

