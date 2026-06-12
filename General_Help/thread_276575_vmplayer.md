---
title: "vmplayer"
date: 2006-10-13
forum: General Help
---

### Post by Crooksey on 2006-10-13
Trying to install, all is well, then:

```


What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include]

```

It wont let me choose that option.

```

uname -r
2.6.15-27-386

```

Any ideas?


..Yes i checked the wiki

---

### Post by angkor on 2006-10-13
Do you have the headers installed for that kernel?

```
sudo apt-get install linux-headers-`uname -r`
```

You will also need the 'build-essential' and 'xinetd' packages.

Read this howto:

[http://www.ubuntuforums.org/showthread.php?t=183209&](http://www.ubuntuforums.org/showthread.php?t=183209&)

---

### Post by Crooksey on 2006-10-13
Thanks, that guide was EXACTLY what i needed, thanks man.

---

