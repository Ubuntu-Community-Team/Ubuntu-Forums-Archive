---
title: "how to delete entry from grub's menu.list?"
date: 2008-06-12
forum: General Help
---

### Post by adredz on 2008-06-12
i have two OSs installed in two different HDs and i want to delete one of those from the grub so that i wont have to choose when i boot my system. ive googled it and no luck...

---

### Post by loell on 2008-06-12
first, backup your menu.lst,

```
sudo cp /boot/grub/menu.lst  /boot/grub/menu.backup  
```

then edit it,

```
sudo gedit /boot/grub/menu.lst
```

if you'd like an entry to be removed it may be better to just comment it by putting ** #**. **ie**

so from
```

title		Ubuntu 8.04, kernel 2.6.24-19-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=415833d5-ed5d-4b5e-840a-1bb71fad68c8 ro quiet splash
initrd		/boot/initrd.img-2.6.24-19-generic
quiet
```

to

```
#title		Ubuntu 8.04, kernel 2.6.24-19-generic
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=415833d5-#ed5d-#4b5e-840a-1bb71fad68c8 ro quiet splash
#initrd		/boot/initrd.img-2.6.24-19-generic
#quiet
```

you'll know that its the right entry , if you match the title that you'd like to remove  in your grub when you boot.

not clear yet? post your **menu.lst** :)

---

### Post by adredz on 2008-06-12
clarong-claro :)

but, the timed grub option is still there. how can i set it up so it won't show during boot up?

---

### Post by VSpike on 2008-06-12
Add the option "hiddenmenu" to the menu.lst file.

---

### Post by adredz on 2008-06-12
all done..thanks!:)

---

### Post by drs305 on 2008-06-12
For future reference, I recommend making the changes via StartUp-Manager. It eliminates the possibility of screwing up menu.lst and has lots of tweaks to grub's menu.lst

For more information on StartUp-Manager and boot displays, please take a look at:
[HOWTO: Grub Menu Kernel Display Options]("http://ubuntuforums.org/showthread.php?t=818177")

Please mark this thread solved via the Thread Tools link at the top right of the original post.

---

