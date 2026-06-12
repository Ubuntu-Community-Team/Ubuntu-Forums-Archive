---
title: "making a live cd????"
date: 2007-09-25
forum: General Help
---

### Post by jrharvey on 2007-09-25
I have Ubuntu exactly the way I like it and with all the programs that I need. I really would like to make a live DVD that I could take to work so I can have ubuntu there. Is this possible???

---

### Post by machoo02 on 2007-09-25
yup....check out [this thread]("http://ubuntuforums.org/showthread.php?t=229625")

---

### Post by pointone on 2007-09-25
You might want to take a look at the bootcd package for this task.

```
apt-get install bootcd
bootcdwrite
```

... will create a live CD copy of your currently running system.

---

