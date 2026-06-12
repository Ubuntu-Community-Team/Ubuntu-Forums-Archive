---
title: "Partitions not visible"
date: 2015-03-17
forum: General Help
---

### Post by anuj_malviya on 2015-03-17
I have installed ubuntu 14.04 on my laptop Lenovo G50-45 having AMD Radeon Processor, 1 TB hdd 8GB RAM.
I did three partitons of same size, but my other partiton other then the root partition is not visible.
1) How can I get this partion disp,layed in the launcher?
I have free DOS in one partiton no windows.
Regards
Anuj

---

### Post by carl4926 on 2015-03-17
Let us see
```
sudo parted -l
```

---

### Post by anuj_malviya on 2015-03-19
HI Thanks for the reply. My intention was to make all the partitons visible just like drives are visible in case of windows. 
I reinstalled ubuntu again and this time I did not do any partition. Allowed ubuntu boot setup to do it . I got 1 gb as swap and rest was ubuntu.

---

### Post by Bashing-om on 2015-03-19
anuj_malviya; Hello;

You are the master of your machine. The system does what you tell it to.
In this case for external-to-ubuntu file systems to be "auto mounted" make an entry in the file system table to make that effect.
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131) <- bodhi.zazen -Understanding fstab
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336) <-Manualy edit fstab - why(Morbius1)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

