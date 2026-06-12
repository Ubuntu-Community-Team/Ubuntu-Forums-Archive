---
title: "Dual Boot Question"
date: 2007-01-27
forum: General Help
---

### Post by shadowfx78 on 2007-01-27
Ok i have been dual booting with (k)ubuntu and windows for sometime and i finally want to remove windows does that mean i have to wipe the hd clean and start all over with the install?

---

### Post by Solver on 2007-01-27
No, you would only need to remove the Windows partitions (and subsequently you'll probably want to merge the newly acquired free space into your Ubuntu partition(s) so you don't waste that space).

---

### Post by shadowfx78 on 2007-01-27
i could do that with the live cd right? just wanna get my plan down so i know what im doing and dont make mistakes ya know.

---

### Post by Solver on 2007-01-27
Yeah, running gparted from the Live CD should work just fine. In fact, you could delete the Windows partitions from your normal Ubuntu install, although you do need the Live CD to merge the free space in.

Oh, be prepared to spend some time on it. If your Windows partitions are located before the Linux ones particularly, resizing the Ubuntu partitions might take a while.

---

### Post by shadowfx78 on 2007-01-27
kinda figured that. I just was thinkin what do i do about grub once that is done?

---

### Post by agustin.g on 2007-01-28
```
 sudo text_editor_of_choice (gedit, vim, nano) /boot/grub/menu.lst 
``` 

delete the lines saying "Other Operating Systems" and "Windows"... **if you want** make a backup ```
 sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
``` and post the original menu.lst here, we'll tell you what you can safely remove

EDIT: other users pls correct me if i'm wrong

---

### Post by shadowfx78 on 2007-01-29
alright everything is all taken care of thanks for your help guys.

---

