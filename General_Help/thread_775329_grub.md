---
title: "grub"
date: 2008-04-30
forum: General Help
---

### Post by blindman4556 on 2008-04-30
i just installed ubuntu hardy, and when i boot my pc all it says is GRUB in the top left corner, i sat and waited and nothing...so the only way i can boot ubuntu is to put in live cd and in the options choose boot from first hard disk....how would i fix it so i dont have to deal with the live cd

---

### Post by hermes0710 on 2008-04-30
> **blindman4556 said:**
> i just installed ubuntu hardy, and when i boot my pc all it says is GRUB in the top left corner, i sat and waited and nothing...so the only way i can boot ubuntu is to put in live cd and in the options choose boot from first hard disk....how would i fix it so i dont have to deal with the live cd

Boot to your ubuntu system the way you do so far (from live cd) and when you log in open a terminal and run ```
sudo grub
```

Then find in which drive the grub is installed:
```
find /boot/grub/stage1
```

Let's suppose it says "hd(a,b)"

Then type
```
root (hda,b)
```
```
setup (hda)
```
```
quit
```

Replace a, b accordingly to the results of the "find" command

---

### Post by blindman4556 on 2008-04-30
that made it work, but now i get grub error 17

---

### Post by hermes0710 on 2008-04-30
Check this out and if it doesn't help come back and give more details on which phase exactly you have the error prompted.

[http://ubuntuforums.org/showthread.php?t=442945]("http://ubuntuforums.org/showthread.php?t=442945")

---

