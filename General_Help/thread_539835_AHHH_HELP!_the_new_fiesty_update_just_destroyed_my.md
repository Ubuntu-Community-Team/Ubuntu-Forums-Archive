---
title: "AHHH HELP! the new fiesty update just destroyed my windows partition!"
date: 2007-08-31
forum: General Help
---

### Post by taehC on 2007-08-31
I just installed the new fiesty update and when i restarted it didnt show my windows partition when i booted up!
i forget how to set it up to show windows on start up
what file do i have to edit?

---

### Post by Lord Illidan on 2007-08-31
I don't think it destroyed your Windows partition...probably just your bootloader, which is strange as I don't recall any updates to Grub lately.

Still, can you post this file here /boot/grub/menu.lst

---

### Post by taehC on 2007-08-31
ya just kidding about destroying it

---

### Post by taehC on 2007-08-31
how do i set the file up when my windows is on the second partition?
i remember where the part goes but all i remember is 
title 
i dont really know what else to do to set it up

---

### Post by Lord Illidan on 2007-08-31
That's why I told you to paste the contents of that file here, so that we can help you set it up :

Here it is again : /boot/grub/menu.lst

---

### Post by taehC on 2007-08-31
```

title           Ubuntu
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8aeb5123-d78f-4b1a-bc$
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=8aeb5123-d78f-4b1a-bc$
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8aeb5123-d78f-4b1a-bc$
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=8aeb5123-d78f-4b1a-bc$
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet

```
that is the list of things that it shows when it boots

---

### Post by Lord Illidan on 2007-08-31
Ok. try adding these lines then :

title           Windows
root            (hd0,1)
savedefault
makeactive
chainloader     +1

---

### Post by taehC on 2007-08-31
AH! yes that was what used to be there. thx so much!

---

### Post by Lord Illidan on 2007-08-31
No problem, next time just remember to give all relevant information when posting, so we can answer faster.

---

