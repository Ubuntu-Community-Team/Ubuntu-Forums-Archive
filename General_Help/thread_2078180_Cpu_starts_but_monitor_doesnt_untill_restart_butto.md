---
title: "Cpu starts but monitor doesnt untill restart button pressed"
date: 2012-10-30
forum: General Help
---

### Post by yasirmahmood on 2012-10-30
hey guys whenever i install any linux distribution especially ubuntu alongwith window then this thing happens that when i turn on my computer my cpu starts but my monitor doesn't display anything and keeps on blinking untill  i press the restart button couple of times or press and hold restart button for few seconds then release it then it shows display .please help me out what this problem reply me quickly thanks in advance

---

### Post by dino99 on 2012-10-30
remove "splash" from /etc/default/grub, then update grub. That let you see the boot comments.

---

### Post by yasirmahmood on 2012-10-30
> **dino99 said:**
> remove "splash" from /etc/default/grub, then update grub. That let you see the boot comments.

hey dear i dont know much about it but as far as my knowledge is if we disable splash screen then at ubuntu logon screen we will not see a graphical interface instead we will see command line interface to login to our user

my problem is that my moniter doesnt start and keeps blinking afterwards when it starts by pressing restart button etc then it workds perfectly whether i login to windows or linux it workds just perfect

---

