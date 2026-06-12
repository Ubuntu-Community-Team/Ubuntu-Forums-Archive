---
title: "[SOLVED] Mount problems"
date: 2007-12-15
forum: General Help
---

### Post by chazz-bg on 2007-12-15
i have problem with ounting cd images , after moving root file system to naother partition , when i try to mount something i get this error 
```
chazz@MetalZone:$ mount -o loop image.iso /media/image/
mount: could not find any device /dev/loop#
```
is there a way to solve the problem or i am f*cked up again :(

---

### Post by taurus on 2007-12-15
```
sudo mount -t iso9660 image.iso /media/image -o loop
```

---

### Post by geirha on 2007-12-15
Sounds like it's unable to load the loop module. Does this give any error message? ```
sudo modprobe loop
ls -l /dev/loop?

```

---

### Post by chazz-bg on 2007-12-15
@geirha this is the answer from that command 
```
chazz@MetalZone:~$ sudo modprobe loop
chazz@MetalZone:~$ ls -l /dev/loop?
brw-rw---- 1 root disk 7, 0 2007-12-15 20:08 /dev/loop0
brw-rw---- 1 root disk 7, 1 2007-12-15 20:08 /dev/loop1
brw-rw---- 1 root disk 7, 2 2007-12-15 20:08 /dev/loop2
brw-rw---- 1 root disk 7, 3 2007-12-15 20:08 /dev/loop3
brw-rw---- 1 root disk 7, 4 2007-12-15 20:08 /dev/loop4
brw-rw---- 1 root disk 7, 5 2007-12-15 20:08 /dev/loop5
brw-rw---- 1 root disk 7, 6 2007-12-15 20:08 /dev/loop6
brw-rw---- 1 root disk 7, 7 2007-12-15 20:08 /dev/loop7
```

@taurus it work with this comand , after ```
sodu modprobe loop
```

---

### Post by chazz-bg on 2007-12-17
bump :(

---

