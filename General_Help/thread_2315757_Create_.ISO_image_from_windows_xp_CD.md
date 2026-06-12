---
title: "Create .ISO image from windows xp CD"
date: 2016-03-02
forum: General Help
---

### Post by midhun4 on 2016-03-02
I need to create a iso image of WIN Xp.I tried using Brasero,but was unable to do it.I am using ubuntu12.04 LTS.What I need is to write a bootable disc of winxp,for that i need to create a iso from winxp cd,pls guide me how can i do it?

---

### Post by bytr on 2016-03-02
Have you tried the "Disks"? It can be used to create an image file from the disk drive.

---

### Post by Bucky Ball on 2016-03-02
What are you trying to create an ISO image of Windows XP from???

---

### Post by midhun4 on 2016-03-02
> **Bucky Ball said:**
> What are you trying to create an ISO image of Windows XP from???

create a iso image of xp from cd ,hope u understand t now!!!!

---

### Post by midhun4 on 2016-03-02
disks is  nt available in software centre,can i install via terminal?

---

### Post by coldraven on 2016-03-02
> **bytr said:**
> Have you tried the "Disks"? It can be used to create an image file from the disk drive.
Using "Disks" you have to select the CD and then use the menu button on the top right of the window.
Or install K3B from the Software Centre.

---

### Post by howefield on 2016-03-02
Thread moved to the "*General Help*" forum.

Even though this thread isn't making much sense...

Try the command line

```
dd if=/dev/cdrom of=file.iso
```

assuming /dev/cdrom is the path where the CD is mounted, and substitute the actual file name instead of file.iso

---

### Post by grahammechanical on 2016-03-02
I do not think that the Disks utility is available for Ubuntu 12.04.

An ISO image is a kind of compressed file. Brasero will create an ISO image of any group of files but it will not be bootable unless we have provided some kind of boot loader such as Syslinux.

The Ubuntu ISO images use either Syslinux or IsoLinux (I am not sure which it is) to load the Ubuntu live session.

Regards.

---

### Post by midhun4 on 2016-03-02
thank u ,pls close the thread

---

### Post by The Cog on 2016-03-02
+1 to howefield (post #7). 
 A .ISO file is a bit-for-bit image of a CD. dd will copy from the CDROM to the .iso file.

Edit: Oops - posting collision.

---

### Post by sudodus on 2016-03-02
Instead of closing the thread please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help other people find your solution.

---

### Post by midhun4 on 2016-03-03
> **sudodus said:**
> Instead of closing the thread please click on **Thread Tools** at the top of the page and mark this thread as SOLVED. It will help other people find your solution.

Sorry for that,But I didnt any solution for it and i tried every possible ways ,so I guess it should be closed rather than marking it as solved!!!

---

### Post by sudodus on 2016-03-03
Did you try howefield's solution?

```
dd if=/dev/cdrom of=file.iso
```

What happened? Was there a problem with the symbolic link? In standard Ubuntu and the Ubuntu family flavours, /dev/cdrom is a symbolic link

```
lrwxrwxrwx 1 root root 3 mar  3 20:52 /dev/cdrom -> sr0
```

and it should work with **/dev/sr0** (directly to the block device)

```
**dd if=/dev/sr0 of=file.iso**
```

If you have another linux distro, you might need another command, but you wrote  Ubuntu 12.04 LTS in post #1, so it should work. If it does not work, maybe the disk or the CD/DVD drive is damaged(?).

---

### Post by midhun4 on 2016-03-04
> **sudodus said:**
> Did you try howefield's solution?

```
dd if=/dev/cdrom of=file.iso
```

What happened? Was there a problem with the symbolic link? In standard Ubuntu and the Ubuntu family flavours, /dev/cdrom is a symbolic link

```
lrwxrwxrwx 1 root root 3 mar  3 20:52 /dev/cdrom -> sr0
```

and it should work with **/dev/sr0** (directly to the block device)

```
**dd if=/dev/sr0 of=file.iso**
```

If you have another linux distro, you might need another command, but you wrote  Ubuntu 12.04 LTS in post #1, so it should work. If it does not work, maybe the disk or the CD/DVD drive is damaged(?).

Thanks a lot ,Voila,This solved t!!!

---

### Post by sudodus on 2016-03-04
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

