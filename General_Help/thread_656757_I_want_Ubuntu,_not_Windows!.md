---
title: "I want Ubuntu, not Windows!"
date: 2008-01-02
forum: General Help
---

### Post by Faust942 on 2008-01-02
I have used Ubuntu before, but I usually formated my computer when I wanted to do this.

I have my system dual booting Windows XP and Ubuntu, I am starting to think switching back to Ubuntu is not a bad idea. 

How would I delete my Windows XP partition, while still being able to boot to Ubuntu? No grub loader or selection screen.

---

### Post by jken146 on 2008-01-02
Format your Windows partition as ext3 and mount it somewhere for storage.  That's the easiest thing to do.

As for GRUB, you'll need to edit /boot/grub/menu.lst -- comment out the Windows entry and uncomment the word "hiddenmenu" near the top of the file.  You'll also probably want to change the timeout option (just above hiddenmenu) to something smaller, e.g. 3.

---

