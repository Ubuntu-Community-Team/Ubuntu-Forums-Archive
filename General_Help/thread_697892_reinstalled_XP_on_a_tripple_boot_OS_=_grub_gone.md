---
title: "reinstalled XP on a tripple boot OS = grub gone"
date: 2008-02-15
forum: General Help
---

### Post by nacho32 on 2008-02-15
ok heres my plroblem I have been runnung a tripple boot os
 on drive C i had win XP installed on the next hard drive , D I had Vista and Ubuntu installed , was working great, the XP got a nasty virus so I reinstalled it, no grub is gone. I used the super grub boot loader cd and I can get it to boot into Linux, only when the cd in in help! I cant get it to find vista either but the oS is still their, any help would be greatful

---

### Post by luisromangz on 2008-02-15
Look for info on how to reinstall grub. You would only need the Ubuntu CD.

---

### Post by PinkFloyd102489 on 2008-02-15
> **luisromangz said:**
> Look for info on how to reinstall grub. You would only need the Ubuntu CD.

Very helpful there. :-P



Here's a guide on how to reinstall grub using the Live CD.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by cabaro on 2008-02-15
Hi Nacho

Can you give the output of
```

sudo fdisk -l
```

Also can you tell which partitions hold Vista and XP?
Which partition is active and where is grub installed?

I'm a noob, but let's see, if i have a clue where to go on this.

Cheers
/cab

---

### Post by cabaro on 2008-02-15
Perhaps...

```

grub

find /boot/stage1
(hdx,x)

root (hdx,x)

install (hd0,0)     #or where you want to install

```

I'm not sure how Vista acts though. I have no exp on that one. I do remeber reading something about it being a little 'cranky' with bootloaders. There were some ways to hack it, but i can look into that earlier, since it's AM here now :)

/cab

---

### Post by nacho32 on 2008-02-15
ok I tryed the first link
 and it told me to type sudo grub
then I type find/boot/grub/stage1
 and get unknown command ?
Im in linux useing the super grub boot loader cd

as technical questions here is what I can tell you I have XP installed on the harddrive C
I have linux and vista on the second hard drive witch is D

---

### Post by nacho32 on 2008-02-16
Ok I got the grub back and I can boot into win xp and Linux, but under window choice menu it use to bring up the vista boot loader , now it just boots to xp , how do I get the vista back in my selection in the grub ?

thanks to all who answered,

---

### Post by nacho32 on 2008-02-16
anyone?

---

### Post by mdurham on 2008-02-16
Hi nacho32, I 'think' that you have to boot from your Vista install disc and repair the Vista boot. Providing that your grub is working ok, you should then be able to boot to the Windows XP/Vista selection menu. I don't understand what goes on between Vista and XP at boot time, it's a bit weird.
Cheers, Mike

---

### Post by nacho32 on 2008-02-16
I tryed that and now vist boots but shows no XP :(

---

### Post by nacho32 on 2008-02-16
ok I was able to edit the vista boot loader , down loaded a tool call vist-boot-pro
this gave me the option to edit the vist boot loader....



so in this fun world of booting multi boot computer , 2 tools are a must, 
1 super grub boot loader
2 vista boot pro

:)

---

