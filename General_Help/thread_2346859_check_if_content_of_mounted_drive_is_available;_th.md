---
title: "check if content of mounted drive is available; then perform action"
date: 2016-12-19
forum: General Help
---

### Post by marchello_lippi2 on 2016-12-19
Hi all, 

My need is to check if content of mounted drive is available at /mnt/folder1/file.txt and then perform [some action] if result is negative. 
Please advise how do I achieve it. 
Thanks ahead.

---

### Post by Habitual on 2016-12-19
Are you asking for shell/script/bash code|logic?
```
if [ -f /mnt/folder1/file.txt ]; then echo 'Exists'; else echo "Do Stuff"; fi
```

Hope that's what you are after. :)

---

### Post by marchello_lippi2 on 2016-12-26
> **Habitual said:**
> Are you asking for shell/script/bash code|logic?
```
if [ -f /mnt/folder1/file.txt ]; then echo 'Exists'; else echo "Do Stuff"; fi
```

Hope that's what you are after. :)


Thanks, seems working, will test it few weeks more :)

---

### Post by Habitual on 2016-12-26
You are welcome.

---

### Post by marchello_lippi2 on 2017-01-20
ok, after some real-life testing I discovered that if mounted drive became available under another device name, then > if [ -f /mnt/folder1/file.txt ]; then echo 'true'; else echo 'false'; fi gives **true**, but ls /mnt/folder1 gives i/o error. 
So, the question so far is, how do I check in script if ls /mnt/folder1 gives i/o error or not? 
Please advise.

---

