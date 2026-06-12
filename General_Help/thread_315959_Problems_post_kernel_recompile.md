---
title: "Problems post kernel recompile"
date: 2006-12-10
forum: General Help
---

### Post by Takmadeus on 2006-12-10
Greetings

I write to talk about a proble which is very, very disturbing

recently I recompiled my kernel from source (2.6.19 from kernel.org) and everything went just fine, yet there was a problem, and it is that after I instakll it and try it, it will not allow me to access windows partititons....how's that:

when I open /media/C (/dev/hda1) as a normal user it will say: 

only root can mount /dev/hda1 in /media/C

when I do that as root it will say:

/media/C already mounted or resource busy


what can I do?.... when I switch to the default kernel it mounts windows partitions normally..... dunno what to do, please help... thanks in advance ;)

---

### Post by CRCarl on 2006-12-10
When you say windows partition, do you mean NTFS? I don't think NTFS is included by default, did you add NTFS support when you compiled your new kernel?

Craig

---

### Post by CRCarl on 2006-12-10
Also, try this[ http://www.psychocats.net/ubuntu/mountwindows]("http://www.psychocats.net/ubuntu/mountwindows")

---

### Post by Takmadeus on 2006-12-10
yep! I added NTFS support in the kernel :( still it does not allow me to mount NTFS partitions..... neither as an user nor as root

by thebway, I already had changed my fstab as pointed in the link you gave me....

---

