---
title: "Live CD and &quot;The folder contents could not be displayed.&quot;"
date: 2008-06-05
forum: General Help
---

### Post by kimolias on 2008-06-05
Hello, my openSuSE 10.3 crashed and I'm trying to backup my files. I'm using Ubuntu 7.10 live cd to do this. Some folders cannot be read because of the old openSuSE permissions. I know the usernames and the passwords. Is there anyway I can access them?

Thank you in advance.

---

### Post by Xiong Chiamiov on 2008-06-05
I haven't done it myself, but you should be able to use
```

sudo -u [username]

```
to do things as one of those users, and use I suppose the chown command (or chmod) to make it so that you can access them normally.

EDIT: If you're not familiar with how those work, I can expand; please just ask.

---

### Post by kimolias on 2008-06-05
```
su -u pek
``` 
echos:
```
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
            { -e file [...] | -i | -s | <command> }
```

Also, what if I want to login as root, but as root of the openSuSE and not as of the Ubuntu live cd (which I cannot do anyway)?

---

### Post by kimolias on 2008-06-05
ok..
```
sudo nautilus
```
did the job ;)

---

### Post by Xiong Chiamiov on 2008-06-05
In the future, though (it shouldn't make a difference on the LiveCD, really), use
```

gksudo nautilus

```
instead, as it prevents some annoying permissions issues.  That goes for any graphical apps you wish to launch as root, btw.  You KDE users, use kdesudo.

---

