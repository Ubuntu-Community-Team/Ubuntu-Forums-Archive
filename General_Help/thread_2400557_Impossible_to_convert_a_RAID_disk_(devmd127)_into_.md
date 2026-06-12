---
title: "Impossible to convert a RAID disk (/dev/md127) into a standard drive"
date: 2018-09-07
forum: General Help
---

### Post by prog-amateur2 on 2018-09-07
Good morning, everyone, 
I have a problem with one of my hard disks in software RAID (with *mdadm*). It was installed in an old computer that I don't need anymore. 

Yesterday, I wanted to delete an external disk with the command *"dd"*. I had a software RAID with something like this: 

```
/dev/sda: my main hard disk 
/dev/md127 : RAID disk
/dev/md/root: I don't know what it was.
```

In short, since this PC was old, and I wasn't sure of my approach, I first (fortunately) saved the data before running the *"dd"* command. 

The problem is that instead of erasing the external hard disk, I erased the main hard disk (*sda*). 

As I said, my data has been backed up so my problem is not the loss of data, my problem is that I can't boot on the second disk. So I wanted to format it using a Live USB Ubuntu, but it's impossible to do because the disk is not well recognized. I can hear the sound of the disc connection, and I can hear the disc rotating, but the only thing displayed is */dev/sda* without any other information and I can only change the mounting point (see photo editing below): 

[IMG]https://preview.ibb.co/gjQU0K/smart.png[/IMG]


How to recover the disk please? I don't mind if it's impossible to recover the disk, but I prefer to recycle it if possible, it is always better to try. 

Thank you very much for your help.

---

