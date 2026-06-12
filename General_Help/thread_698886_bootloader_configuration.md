---
title: "bootloader configuration"
date: 2008-02-16
forum: General Help
---

### Post by bookworm_2008 on 2008-02-16
How do I extend the time on the bootloader before it starts the default OS on the list?

How can I change the order or the default OS on the list?

---

### Post by 444 on 2008-02-16
Edit /boot/grub/menu.lst

There is a "timeout" option in there where you can enter the seconds.

---

### Post by kuja on 2008-02-16
You'll need to edit the file /boot/grub/menu.lst (ie: sudo editor /boot/grub/menu.lst)

Look for this line:
```
timeout 10
```

Change it to whatever length you want, it's in seconds.

To change the order just scroll all the way down to the bottom where the menu entries are and copy and paste the blocks around, though, any Ubuntu related ones will be magically put back into there original form on bootup.

To change the default entry look for a line like this:
```
default 0
```
Just change the number - count down from the top of the list starting with 0.

---

### Post by bookworm_2008 on 2008-02-16
Thanks for all the feedback and so quick too!

---

