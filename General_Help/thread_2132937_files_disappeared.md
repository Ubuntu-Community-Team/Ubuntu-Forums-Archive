---
title: "files disappeared"
date: 2013-04-06
forum: General Help
---

### Post by goncalocg on 2013-04-06
Hello! I have one partition for windows, another for Ubuntu and another for my files...Mainly I only use Ubuntu...

Today almost 80% of my files in the 3rd partition disappeared without any reason or sense whatsoever...I didn't erased them, there's nothing in the TrashBin...

What can I do!?

---

### Post by goncalocg on 2013-04-06
and also, now I only have there 17gb and in the DiskVolumeInformation says I have 80gb...though I had 120gb before...thank you

---

### Post by Bashing-om on 2013-04-06
goncalocg; Hi !

At this point one can not say. However one can mount that partition form the terminal and have a look-a-bout the files that are currently on that partition. (assuming that partition is formatted for ubuntu format, else the mount commands may have to be adjusted accordingly)
```
sudo fdisk -l
``` to identify the partition:
```
ls -la /media
ls -ls /mnt
``` to identify any pre-existing mount points for the "data" partition in question:
```
sudo mkdir /mnt/data ## makes a new mount point IF no other exist
sudo mount /dev/sda3 /mnt/data ##attach the partition to the file system change sda3 to the actual partition identifier
ls -la /mnt/data ##to see the listing of all directories and top files on that partition
ls -la mnt/data/<some_other_directories> ##a-look-around
```
Remember MUST (un-)mouint that partition manually when done prior to shutting your system down. Failure to do so will result in system corruption at some level. UNMOUNT ->
```
sudo umount /mnt/data
```

In the event further advise is needed, please inquire ![INDENT=2]
just try'n to help

[/INDENT]

---

### Post by goncalocg on 2013-04-06
alright, thanks a lot for your answer man!!!

I will see If I can sort anything out, and reply again..thank you again.

---

### Post by goncalocg on 2013-04-06
I just didn't understand one thing:

I have to unmount it first, then apply those commands?

---

### Post by Bashing-om on 2013-04-06
goncalocg;
Apologies, was not thinking to clearly. If that partition is auto mounted -data partitions are often not auto mounted-  in /etc/fstab, then there is no need to mount it again (manually that is). Just use the path as provided in the /etc/fstab file to list anything in terminal on that partition.
[INDENT=3]hope this helps

[/INDENT]

---

