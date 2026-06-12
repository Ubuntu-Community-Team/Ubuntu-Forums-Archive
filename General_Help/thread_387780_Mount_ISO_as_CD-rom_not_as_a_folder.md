---
title: "Mount ISO as CD-rom not as a folder"
date: 2007-03-18
forum: General Help
---

### Post by ADloser on 2007-03-18
Can anyone tell me how I can mount an ISO image as a CD and not as a folder.
Is there an easy way to do this without installing some program like cdemu?

 Thanks!

---

### Post by taurus on 2007-03-18
Everything in Linux is a directory.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/iso
sudo mount -t iso9660 -o loop filename.iso /media/iso
df -h
```

---

### Post by ADloser on 2007-03-18
Thanks for the quick reply!
How do I know if this was successfully mounted as a CD?

When I open my file browser it doesn't have the CD icon.
and the application I'm trying to run still doesn't read this as a CD.

---

### Post by taurus on 2007-03-18
Your filename.iso is mounted to /media/iso so point your filemanager to /media/iso.  Otherwise, run this command from a terminal.

```
ls -la /media/iso
```

---

### Post by llamakc on 2007-03-18
> **ADloser said:**
> Thanks for the quick reply!
How do I know if this was successfully mounted as a CD?

When I open my file browser it doesn't have the CD icon.
and the application I'm trying to run still doesn't read this as a CD.

what** application** are you trying to run?

---

### Post by ADloser on 2007-03-19
taurus: thanks again.
I can see the folder and I can access the files, but I do not think that my computer "sees" it as a CD in a virtual drive, which is ultimately what I am after.


llamakc:
Warcraft III, I share a CD with my roommate and when I mount it with DAEMON in windows it has no problems.

---

### Post by MattThLinuxNewb on 2008-03-17
hey im pretty sure your problem is that you havent added the mount point as a drive under wine.
in the console type
```
winecfg
```
then go to the drives tab, then click the add button and change its directory to the mount point of the CD e.g. /media/gameCD/ or whatever.
I realize this is an old post but thought id just mention this to save everyone else doing something similar the hassle... :)

---

