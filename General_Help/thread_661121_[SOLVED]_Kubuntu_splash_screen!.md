---
title: "[SOLVED] Kubuntu splash screen!"
date: 2008-01-07
forum: General Help
---

### Post by snakeeyes on 2008-01-07
Hi, can some one please tell me how to remove the splash screen for Kubuntu so I can see the processes loading. It looks better, more Unix like ;)

I tried what I know by going in the GRUB configuration menu I removed the option "splash" and "quiet" from the bottom of the kernel entry. That didn't work as there a blank screen while boot up.

I am using kernel 2.6.24-2-generic. Has something changed or what? I am not a new user, but normally in other distros u could just press escape so thats why I am asking.

Thanks!

---

### Post by snakeeyes on 2008-01-08
no one?

---

### Post by Kingsley on 2008-01-08
Try adding splash=verbose to the kernel line in /boot/grub/menu.lst.

---

### Post by kvonb on 2008-01-08
-

---

### Post by snakeeyes on 2008-01-08
sorry both the suggestions don't work, any other ideas?

---

### Post by fish2ways on 2008-01-08
Remove  'splash'  from menu.lst

/boot/vmlinuz-2.6.22-14-generic root=UUID=9bc2dba2-5c44-4f12-b022-5983943b07bf ro quiet _splash_

---

### Post by snakeeyes on 2008-01-08
I just noticed I don't have the quiet option before splash, does that do anything?

---

