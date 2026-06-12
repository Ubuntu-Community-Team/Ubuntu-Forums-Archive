---
title: "Unable to exclude directory using zip compression"
date: 2015-07-19
forum: General Help
---

### Post by peter1897 on 2015-07-19
I am trying to compress the home directory of user max. Inside the max directory there is a directory **share** which i want to exlude but i am unable to. These are to commands i tried but they didn't worked, it still includes the **share** directory when i run the command:
```
max@ubuntu:/home$ sudo zip -r max.zip max -x "/home/max/share/*"
max@ubuntu:/home$ sudo zip -r max.zip max -x /home/max/share/**\*
max@ubuntu:/home$ sudo zip -r max.zip max -x /home/max/share/*\*
max@ubuntu:/home$ sudo zip -r max.zip max -x /home/max/share/\*

```

Any idea why it doesn't work?

---

### Post by Lars Noodén on 2015-07-19
You are using a relative path when telling zip what to compress, so you could use a relative path for the exclusion as well.

```

sudo zip -r max.zip max -x "max/share/*"

```

---

### Post by peter1897 on 2015-07-19
Thanks, the relative path was the problem. I guess i have to use relative paths for everything or absolute paths for everything, otherwise it won't work. These both commands worked:
```

sudo zip -r max.zip /home/max -x "/home/max/share/*"
sudo zip -r max.zip max -x "max/share/*"
```

---

