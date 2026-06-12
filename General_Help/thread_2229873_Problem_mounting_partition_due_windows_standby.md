---
title: "Problem mounting partition due windows standby"
date: 2014-06-15
forum: General Help
---

### Post by Hesediel on 2014-06-15
Hello my problem is that every time i startup xubuntu (with ubuntu the same) i have the windows partition that does not start.

i can solve this problem doing this comand on the terminal

```
sudo mount -t ntfs-3g -o remove_hiberfile /dev/sda2 /media/Windows
```


I have disabled on windows the fast startup but the problem isn't solved... i am getting bored to see the unable to mount ecc every start. How can i solve this?

---

### Post by veddox on 2014-06-16
Do you shut down Windows properly every time, or do you use hibernate?

When a Windows system is hibernating, Ubuntu will refuse to mount it, overriding that with the command you gave is not advisable:

> Whether you write to your Windows C:\ partition or a shared NTFS data partition, be aware that if you are using Windows 7, and Windows 7 is in a hibernated state when you write to the NTFS partition from Ubuntu, you will lose all your changes. This is because when Windows 7 is hibernated it writes the system state to a file stored on disk and restores from that file when the system is re-awakened, thus restoring the whole fileystem to a state before any changes made from Ubuntu. In Windows 7 you must avoid using hibernation.
Source: [Mounting Windows Partitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

---

### Post by Hesediel on 2014-06-16
yes i shutdown properly

---

