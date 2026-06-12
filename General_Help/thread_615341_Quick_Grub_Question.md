---
title: "Quick Grub Question"
date: 2007-11-17
forum: General Help
---

### Post by oneadvent on 2007-11-17
Ok, so what if I delete /boot/grub/menu.lst and then type update-grub in the terminal?

I only have one OS on this system. (Ubuntu)

---

### Post by integr8e on 2007-11-17
Why in the world would you want to do that?  Just for experimentation purposes?

---

### Post by oneadvent on 2007-11-17
Kinda :lolflag:

I do have another motive though. I did a few partioning and reinstalling things and ended up with it saying I have an install on sda1. 

I do not even want to see this menu, and I never used to...those were the good days. I only use Linux, I do not need to boot into anything else.

So another words I want to "reset" Grub...then I wondered if it were possible this way.

---

### Post by integr8e on 2007-11-17
You could delete your menu.lst entry and reinstall GRUB (sudo aptitude reinstall grub), but it will not be configured.  I would suggest installing StartUp-Manager (startupmanager) from the repos and using it to reconfigure GRUB.  You can also check out Qqmike's [**HOW TO: GRUB Methods - Toolkit**](http://kubuntuforums.net/forums/index.php?topic=3081671.0).

---

### Post by oneadvent on 2007-11-17
Well Startup Manager worked fine. I guess I dont understand what 

```
sudo update-grub

```

does.

---

### Post by integr8e on 2007-11-17
I've actually just had an experience of my own dealing with GRUB; an experiment I performed last night corrupted my GRUB entry, and I've just managed to repair it  a few minutes ago.  Apparently the "sudo update-grub" command basically rebuilds/updates your GRUB entry in case  you install a new hard drive or something of that nature.  Before you can perform its action, however, you have to have a /boot/grub directory (it *can* be empty, but *must* exist).  Another command is "sudo grub-install [location]" (such as "sudo grub-install hd0" or "sudo grub-install /dev/sda" (or fda), they're both the same).  It completely rebuilds your GRUB entry, which was useful for me because mine had broken.

---

### Post by meierfra on 2007-11-17
> ok, so what if I delete /boot/grub/menu.lst and then type update-grub in the terminal?

do not even want to see this menu, and I never used to...those were the good days. I only use Linux, I do not need to boot into anything else.


Yes, deleting menu.lst  followed by "sudo update-grub" will create a new menu.lst. 
(update-grub is used during every kernel upgrade to update the file "menu.lst")  

Edit:  I just noticed that you already solved your problem via the start up manager, so you can ignore the rest of this post)

Although instead of deleting "menu.lst" I recommend to rename it:

```

cd /boot/grub
sudo mv menu.lst menu.lst.backup

```


Actually the best way to accomplish your goal would be:

open menu.lst via


```
gksudo gedit /boot/grub/menu.lst
```


and change

"timeout 10" to "timeout 3"  
(don't use timeout 0, otherwise you won't be able to get into recovery mode)

and 

"#hiddenmenu" to "hiddenmenu"

After these changes you would  have to press "Esc"  to see the grub-menu.

---

### Post by oneadvent on 2007-11-18
> **meierfra said:**
> 
"#hiddenmenu" to "hiddenmenu"


Although your entire post was insanely useful and informative, the above command is exactly what I was looking for. I changed it immediately.

I am a huge fan of not seeing an option unless I want to use it.

Josh

---

