---
title: "Accessing a crashing window's partition?"
date: 2008-05-01
forum: General Help
---

### Post by Mogurijin on 2008-05-01
I have a machine in which Windows will constantly crash at boot up (blue screen, registry error, etc, etc). Anyways, I wanted to use my Ubuntu liveCD and gparted to reformat and partition the drive.

However, if Windows does not shut down properly I can't access the Windows partition. By the way, is this an Ubuntu or a Windows thing?

Does anyone know of a way to get around this restriction? Or should I take a magnet to the hard drive? Just kidding :)

---

### Post by upthelum on 2008-05-01
You could try using the windows cd and go through system repair and type fixmbr, which may recover the windows boot loader.

---

### Post by Mogurijin on 2008-05-01
The problem lays in the registry, so the blue screen appears right about when the log on would show up. The install is hosed and needs to be redone. Also, using the Windows CD doesn't do much good since I guess the install program crashes when trying to access the partition. By the way, this isn't my computer, nor is it physically in front of me.

---

### Post by Daan on 2008-05-01
```
However, if Windows does not shut down properly I can't access the Windows partition. By the way, is this an Ubuntu or a Windows thing?

Does anyone know of a way to get around this restriction?
```

Hi. :)

Do you mean accessing the Windows partition with gparted? Can't gparted see it? What errors do you get?

---

### Post by upthelum on 2008-05-01
> **Mogurijin said:**
> The problem lays in the registry, so the blue screen appears right about when the log on would show up. The install is hosed and needs to be redone. Also, using the Windows CD doesn't do much good since I guess the install program crashes when trying to access the partition. By the way, this isn't my computer, nor is it physically in front of my.

You could try a tool like Hiren's boot cd to try and rescue the disk. Failing that i would just pop in the Ubuntu cd and fresh install. I would keep regular backups too in case the drive fails.

---

### Post by Mogurijin on 2008-05-01
I think the point might have been missed. Windows WILL NOT shutdown properly, it just keeps crashing. This means the partition it was on can not be accessed through Ubuntu. Gparted can see it, but not do anything with it (such as resizing). Ubuntu can not install on the partition since it can not format or do anything to the partition.

---

### Post by upthelum on 2008-05-01
Thats were Hirens might help you as you can format the drive with it. Failing that i'm not sure why you cant stop windows, if you power down it's stopped, if nothing works maybe the disc is trashed.

---

### Post by Mogurijin on 2008-05-01
Okay, I'll try the Hirens disc. And I can't stop Windows becuase before anything can be done, a blue screen occurs. This forces you do a hard shutdown.

Also, a bad hard drive was suspected, but I'd like to test it first, as I think it is only a screwed up registry. 

Thanks for your help so far ^^

---

