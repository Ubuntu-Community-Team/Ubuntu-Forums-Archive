---
title: "Run Java program as background process"
date: 2012-11-20
forum: General Help
---

### Post by Alan_D. on 2012-11-20
Hello everyone,

I've got a pretty special question today. I have a regular Java application that I want to run on a linux-based server. The program is started via command-line-only SSH, which works well.

The problem is, however, that I need the program to keep running, even if there is no user logged into the system. How would you do that on command line? Any hints? I tried to find answers on Google but it's pretty hard to search for something when you do not really have a significant term for it.


Thank you,


Alan

---

### Post by SlugSlug on 2012-11-20
there is a few ways 

best is probably set it up as a service and have it run at boot google update-rc.d

otherwise you could run it with screen or nohup

```
nohup /path/to/script
```

```
screen /plath/to/script
```


```
screen -r
```

to recall it

---

### Post by Alan_D. on 2012-11-20
@SlugSlug  Thank you, I'm going to try the "screen" option, looks promising :)

---

### Post by SlugSlug on 2012-11-20
you could make your script use screen and then run it via init.d so it loads at boot

thats what I use

---

