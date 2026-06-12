---
title: "boot details"
date: 2007-06-24
forum: General Help
---

### Post by jrev on 2007-06-24
Hi all,

How can I visualize  the boot process with feisty as I could with dapper Drake ?

Thanks for the tip :p

---

### Post by jimbob on 2007-06-24
Have you tried removing the quiet and splash parameters on the kernel line in /boot/grub/menu.lst?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="1"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by jrev on 2007-06-25
[QUOTE=jimbob;2904952]Have you tried removing the quiet and splash parameters on the kernel line in /boot/grub/menu.lst?

Thanks for this good answer Jimbob :)

---

### Post by darkazurka on 2008-06-04
There were 2 quiet options. The 1st after 'ro' and before 'splash'. The 2nd one at a new line of itself after the previous line "initrd".

I removed both quiet options.

---

