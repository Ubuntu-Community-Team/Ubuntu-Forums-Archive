---
title: "Where to call this startup script ?"
date: 2006-12-13
forum: General Help
---

### Post by viluve on 2006-12-13
Hi hi,

I have created a script that allows me to choose which xorg.conf file to use.

I need this script to be called WHEN XSERVER FAILS to start due to invalid video driver. 

My question is, where (from what file/script) should I call this script from?

Name of the script: myscript

thanks in advance

---

### Post by taurus on 2006-12-13
Move it to /usr/bin so it would be in your path so you can call it anywhere you want...

```
sudo mv myscript /usr/bin
```

---

