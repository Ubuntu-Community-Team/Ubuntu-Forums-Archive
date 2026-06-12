---
title: "I need help configure the cube in compiz"
date: 2006-08-16
forum: General Help
---

### Post by onesojourner on 2006-08-16
I have looked and looked and I can't figure out how to mess with the configuration of the cube plugin. I ran gconf-editor and get down to compiz>plugins>cube>options but then what do I do. how do change the veiw to inside the cube and add a background picture? Im sure there is a good right up I just over looked it.

---

### Post by 3rdalbum on 2006-08-16
```
sudo apt-get install gset-compiz
```

It also helps you transform your jelly-like windows into something that won't make you seasick!

---

### Post by onesojourner on 2006-08-16
that installed ok but how do I launch it? typing gset-compiz in terminal does nothing.

---

### Post by panurge77 on 2006-08-16
Gset-compiz is outdated afaik. The entries you want in gconf are in apps>compiz>plugins>cube>screen0>options
check the "in" and "skydome" options

---

### Post by onesojourner on 2006-08-16
> **3rdalbum said:**
> ```
sudo apt-get install gset-compiz
```

It also helps you transform your jelly-like windows into something that won't make you seasick!

> **panurge77 said:**
> Gset-compiz is outdated afaik. The entries you want in gconf are in apps>compiz>plugins>cube>screen0>options
check the "in" and "skydome" options


I dont see an option for skydome, am I missing something?

---

### Post by slikvic2002 on 2006-08-24
Yea, I have the same problem as Onesojourner, the skydome options are not in the Gconf - apps>compiz>plugins>cube>screen0>options. I read somewhere else I might not have the skydome plugin installed. How do I get it?

---

### Post by ayoli on 2006-08-24
gset-compiz from [http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/]("http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/")
 works fine for me, i can launch it from the tray icon menu, or from a console.
regards.

---

