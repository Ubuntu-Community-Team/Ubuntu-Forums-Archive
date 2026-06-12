---
title: "Editing the GRUB menu"
date: 2006-10-30
forum: General Help
---

### Post by Zdravko on 2006-10-30
After I upgraded from Dapper to Edgy, my GRUB menu got expanded with one more kernel. How can I delete all of the previous choices and leave only the current edgy kernel, safe mode, memtest and WinXP? I would also like to have WinXP boot first by default, and this after 5sec time-out.

---

### Post by shawnbishop on 2006-10-30
Good Day

do the following

# sudo vi /boot/grub/menu.lst

Here you can change the boot order as well as hash out the entries you dont want

Cheers

---

### Post by muusikko on 2006-10-30
you can remove the old kernel packages in synaptic package manager. the names of the packages start with linux-. maybe the names are linux-image-* linux-restricted-modules* and linux-headers*
be careful, you have to delete older versions..

synaptic updates also grub automatically.

---

### Post by Zdravko on 2006-10-30
Ok, I will try it.

---

### Post by Zdravko on 2006-10-30
And it works... flawlessly! Thank you very much, [shawnbishop]("http://ubuntuforums.org/member.php?u=110736").

---

