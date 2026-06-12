---
title: "Mount 2nd HDD in Ubuntu 16.04"
date: 2017-12-08
forum: General Help
---

### Post by neeraj.2511 on 2017-12-08
Dear Sir/Madam,

I am Neeraj. I am a software engineer. I need help regarding mounting/partitions of the disk.
I have core i7 machine ubuntu 16.04 LTs Os and 2 disks (SSD as primary and HDD as secondary).
SSD already mounted but I  have to mount 2nd Disk HDD.
Can you help me?


Thanks
Neeraj

---

### Post by Bashing-om on 2017-12-08
neeraj.2511; Hello - Welcome to the forum .

Show us what you are working with , 
Post back - Between Code Tags - the out puts of terminal command:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

sudo parted -l

```
and tell us the manner you want to mount this 2nd drive .

[INDENT][INDENT]there is a process
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-12-08
Open the Program called Files.
Look over at the left side pane and the bottom section should list the external storage devices, including the partitions for the hdd.
Simply clicking on the device you want and the system will automatically mount it.
That's the basic way.

Do you need help setting it up in a more advanced way?

Ninja'd; follow Bashing-om's advice if you need a more advanced way than what I've posted, thus far.

---

