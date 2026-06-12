---
title: "Start hdparm as a service"
date: 2008-05-01
forum: General Help
---

### Post by Bluecube on 2008-05-01
For some reason I don't have hdparm starting as a service. Can anyone please advice of a **simple** way to have hdparm start at startup.

Thanks

---

### Post by Vivaldi Gloria on 2008-05-01
I added some spindown lines to hdparm.conf and after the next boot they just worked. Don't know how but it starts.

---

### Post by Bluecube on 2008-05-02
No one? Surely someone out there can advise!

---

### Post by Zorael on 2008-05-02
Doesn't it add itself as a service? At least it did in Gutsy. Then I grabbed **sysv-rc-conf** from the repositories, ran it and flagged it as S (makes it, uh, start early).

---

### Post by Bluecube on 2008-05-02
Silly question - I've got sysv-rc-conf myself. Hdparm is actually called hdparm and not something obscure is it? Cause I can't see it anywhere.

---

### Post by bingoUV on 2008-05-02
I don't know the answer to your question, but why don't you add the command to /etc/rc.local ? It will be run on every boot, like I have added the following line to mine : 
```

hdparm -B 254 <device>

```

---

