---
title: "Change usplash in Edgy?"
date: 2006-11-29
forum: General Help
---

### Post by jakev383 on 2006-11-29
Just wanted to know if anyone has changed their usplash with Edgy yet? Does the old how-to work? I liked the fbsplash thing, but it looked rather complicated with having to recompile the kernel and all. And most of the posts about those are for the older versions and show problems with Edgy later in the threads.
So, anyone been brave yet?

---

### Post by LLRNR on 2006-11-29
Hi, I used Dapper until 2 days ago, when I installed Edgy... I liked everything except the silent usplash (correct me if I'm wrong, but this is what I understand from your post - that you want to modify the boot splash screen, or however that's called).

If so, then the procedure is quite simple: you have to do a backup of your /boot/grub/menu.lst file and then edit it: You'll notice a section that should be something like this:
```
title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash

```

If you just want the old Dapper usplash back, then remove the **quiet** word; if you want only a text-based boot, then make **ro quiet splash** look like **ro**.

Save the file and reboot...

LLRNR

---

### Post by jakev383 on 2006-11-30
Thanks for the reply. Close to what I was looking for. Mainly interested to see if anyone else has changed the graphics for their boot splash.

---

### Post by muzaki on 2006-12-01
i made my own grub splash(image)+ usplash theme to complete the mac os look on my ubuntu, but still everytime i compile usplash theme which contain transparent png files, the transparent part become black instead of transparent ,i think there's some problem with 
pngtousplash since some ppl have the same problem with me, just wondering if anyone here manage to compile transparent png`s

---

