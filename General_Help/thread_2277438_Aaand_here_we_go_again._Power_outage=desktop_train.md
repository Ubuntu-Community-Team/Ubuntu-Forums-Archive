---
title: "Aaand here we go again. Power outage=desktop train wreck"
date: 2015-05-08
forum: General Help
---

### Post by adambond on 2015-05-08
Had a storm. Power went out. 

when power came back on, I started the computer. 

It booted up just fine. Except, my desktop image is different. The icons are scattered all over. [COLOR=#ff0000]And my cairodock is GONE. [/COLOR]

Wouldnt be a problem, except the cairo dock is the only way I know how to get anywhere in this piece of crap ubuntu system. 

How do I get my cairodock with all my applets and what no, back?

---

### Post by cariboo on 2015-05-08
[s]So you are calling your system names, because you don't know how to use it?[/s] What have you tried already? I'd suggest you run fsck on the / and /home partitions using the following command which will usually solve the problem:

```
sudo fsck /dev/sdxX
```

where /dev/sdxX = the partition you are having a problem with. For example:

```
fsck /dev/sda1
```

which runs on the first partition of the first hard drive in your system.

---

