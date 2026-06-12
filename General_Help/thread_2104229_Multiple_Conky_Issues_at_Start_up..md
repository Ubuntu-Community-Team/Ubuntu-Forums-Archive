---
title: "Multiple Conky: Issues at Start up."
date: 2013-01-12
forum: General Help
---

### Post by 1991sudarshan on 2013-01-12
I have multiple conky configuration. I followed the procedure from crunchbang.com. I intended for 4 conky but during the start up I get 5 conky, the unwanted conky is the default conky. I don't know how it comes during start up alone. It doesn't come when the script is initiated through the shell. 



[IMG]http://imageshack.us/a/img600/9366/conky1.jpg[/IMG]


[IMG]http://imageshack.us/a/img688/3456/conky2.jpg[/IMG]


conky_start

> #!/bin/bash
conky -dc ~/.conky/.conkyrc_clock &
conky -dc ~/.conky/.conkyrc_sys &
conky -dc ~/.conky/.conkyrc_net &
conky -dc ~/.conky/.conkyrc_proc

---

### Post by SlugSlug on 2013-01-14
my guess would be you have another conky running at startup thats using the default /etc/conky/ (eg just the plain conky command will do this)

Have you checked through startup applications & check

```
crontab -l
```

---

### Post by 1991sudarshan on 2013-01-15
> **SlugSlug said:**
> my guess would be you have another conky running at startup thats using the default /etc/conky/ (eg just the plain conky command will do this)

Have you checked through startup applications & check

```
crontab -l
```

```

kevin@kevin-desktop:~$ crontab -l
no crontab for kevin
kevin@kevin-desktop:~$ 

```

My multiple conky is behaving erratic. 

See this conky snapshot. The fourth conky is not running at all

---

