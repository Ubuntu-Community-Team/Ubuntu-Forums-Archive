---
title: "I cant empty trash?!"
date: 2008-06-01
forum: General Help
---

### Post by rine238 on 2008-06-01
HI

I have a stupid little problem, I can't empty trash because there is in one folder where are files with access only permission. I tried to restore it back, but they can not be moved. Is there any command for terminal which could help? Restarting of system did not help.

Thanks for help! :D

---

### Post by zvacet on 2008-06-01
```
cd /home/username/.local/share/Trash/files
```

Once you are inside you can use **ls** command just to see files you want to remove and after that still in that folder run command

```
sudo rm -r *
```

That will empty your Trash.

---

### Post by rine238 on 2008-06-01
> **zvacet said:**
> ```
cd /home/username/.local/share/Trash/files
```

Once you are inside you can use **ls** command just to see files you want to remove and after that still in that folder run command

```
sudo rm -r *
```

That will empty your Trash.

Thank You, this works!

---

### Post by borge22 on 2008-07-03
Thx man! I had the same problem. Worked for me too!

---

### Post by miteshanand1729 on 2008-07-03
Me too have same problem... Worked for me too. thanx....

---

