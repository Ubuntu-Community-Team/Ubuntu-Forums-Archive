---
title: "How do i stop the mdadm --monitor function?"
date: 2018-07-25
forum: General Help
---

### Post by viktor-balogh2000 on 2018-07-25
I set up mdadm to send an email in case of an error, but now I want to disable it. How could I do it?
I used this command: 
```
mdadm --monitor --daemonise --mail=<e-mail adderss> /dev/md0
```

---

### Post by #&amp;thj^% on 2018-07-26
You can control startup behavior on Ubuntu with:
```

dpkg-reconfigure mdadm
```
^^^^I think the above would be the easiest.
Else something like:
```
# /etc/mdadm/mdadm.conf
ARRAY <ignore> UUID=xxxxxxxx:xxxxxxxx:xxxxxxxx:xxxxxxxx

```

---

