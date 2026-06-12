---
title: "need help with grub"
date: 2007-06-14
forum: General Help
---

### Post by GoatFounDeR on 2007-06-14
Hi,

I installed ubuntu 7.04 on my computer with no problems. Then i installed windows again so
my grub got over written (i was expecting that), so i installed grub again with the hope that 
it would detect my windows, and give me a option in the grub menu. But it does not work like 
that i guess.

Can some one tel me what i have to edit or run to get my windows back? I am new to ubuntu 
but not so new to linux. I looked at the grub .conf files, but its a lot more complicated than 
other distros i have used, or ubuntu puts it in a weird place maybe?

any help would be appreciated

GoatFounDeR

---

### Post by bashologist on 2007-06-14
Follow the examples in "/boot/grub/menu.lst".
> # examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
Replace hd0,0 with whatever partition it's on. hd0,0 is the first partition on your first hdd. hd1,0 would be the first partition on your second hdd.
```
# So, you could do something like this:
gksudo gedit /boot/grub/menu.lst

# Then add to the bottom:
title		Windows Xp Professional
root		(hd0,0)
makeactive
chainloader	+1

```

---

### Post by GoatFounDeR on 2007-06-14
Thank you for the help... I cant believe i missed that.
Every thing is working now as it should :)

---

