---
title: "howto get files off my old hard disk safely?"
date: 2008-06-12
forum: General Help
---

### Post by breadbin on 2008-06-12
Hiya, I have Ubuntu Hardy Heron running now on a single sata hd and love it but need to copy music and whatever from my old hard disk onto this new system. The old disk had Mandriva and Win2K dual booting. 

I'm wondering is it safe to simply plug the other hd into mobo  and if I do which one will GRUB boot from? and is there a chance I can damage my current system. 

They're both sata drives. Does it matter which sata port they're in? 

tia

---

### Post by skymera on 2008-06-12
Damaging? No, i doubt it will damage it.

Plug it in and im sure it will boot from your Ubuntu HDD.

Once Ubuntu is loaded you will need to mount the new drive.

First we create a directory to mount it to, lets call it music.

```
 sudo mkdir /media/music 
```

Now you need to check the disks, NOTE: lower case L

```
 sudo fdisk -l 
```

If your drive is sdb1 then we do this
```
 sudo mount /dev/sdb1 /media/music 
```

Change sdb1 accordingly

---

### Post by breadbin on 2008-06-12
> **skymera said:**
> Damaging? No, i doubt it will damage it.


I like the way you won't say definitely no it wont;) I will give that a go thanks and will let you know how I get on. i hope my next post won't be from the laptop!

---

### Post by skymera on 2008-06-12
xD No, it won't damage it. At most your PC will try to boot from it.

Hope everything goes well.

---

### Post by bingoUV on 2008-06-12
Why take the risk of making your PC boot with it? Go into your BIOS settings and make it boot from Ubuntu hard disk.

---

### Post by RichardG891 on 2008-06-12
Or boot from a live CD image such as knoppix and copy your files.

---

