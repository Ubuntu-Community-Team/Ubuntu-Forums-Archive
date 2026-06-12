---
title: "how to become root or change permissions?"
date: 2014-01-12
forum: General Help
---

### Post by lizpy66 on 2014-01-12
Downloaded Floola to see if that would work with my ipod and it wouldn't open so I looked up  why and someone said on floola's forums to put it in usr/local/bin but it won't let me move it there so i tried changing permissions so I can't put it there so how do I change permissions or become owner/root to put it there? I'm on Ubuntu 13.10

Thanks in advance :)

---

### Post by bluefrog on 2014-01-12
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Iowan on 2014-01-12
Punctuation doesn't cost extra ;)
Have you tried it with **sudo**?

---

### Post by lizpy66 on 2014-01-12
Sorry Iowan just woke up haha

How would I do that? I know what sudo does but how would I use it for changing permissions or being root?

---

### Post by tgalati4 on 2014-01-12
Generally, you put floola on the ipod (in the top directory) and when you plug in your ipod you navigate to the top directory of it and double-click *floola* to run it.  This allows *floola* to run on any machine (of the same architecture, 32-bit won't run on 64-bit, mac floola won't run on linux floola, etc).  Although you can run floola locally, the database is then stored on your PC instead of on your device.  That becomes a problem if you have more than one ipod.

Regardless, to get root permissions you need to log in with super user privileges:

```
sudo su
```

*Exit* to exit the session.  Once in the root session you can copy files and change permissions.  Make sure floola is marked as executable:

```
sudo chmod +x floola
```

---

