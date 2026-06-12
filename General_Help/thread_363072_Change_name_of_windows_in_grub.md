---
title: "Change name of windows in grub?"
date: 2007-02-16
forum: General Help
---

### Post by kramer65 on 2007-02-16
Hello,

I've been using ubuntu for a couple weeks now and I'm getting happier and happier with it. Now I would like to change the name of Windows in grub to something else so you cannot see anymore that I have windows but that you can still select it. So that when grub opens you see ubuntu, and you see under it something like "other" or "blabla" which would lead you to windows..

Is this possible? And if so .. how?

---

### Post by llamakc on 2007-02-16
Yes. You need to edit the /boot/grub/menu.lst file.

Do this:

Open a Terminal.

Type:

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.mybackup

sudo gedit /boot/grub/menu.lst

Find the entry for Windows at the bottom and edit the line that says


title Windows XP

to

title WHATEVER_YOU_WANT

---

### Post by kramer65 on 2007-02-16
Alright! Works perfect!

Thanks a lot!

---

### Post by meng on 2007-02-16
Mmmm, it's almost as if you're ashamed to reveal that Windows exists on the computer ...
:D

---

