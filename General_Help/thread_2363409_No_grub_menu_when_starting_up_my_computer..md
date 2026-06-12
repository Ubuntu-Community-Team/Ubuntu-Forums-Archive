---
title: "No grub menu when starting up my computer."
date: 2017-06-09
forum: General Help
---

### Post by sadpotato on 2017-06-09
I am new to xubuntu and linux in general is there supposed to be a menu when starting computer because for me it's just a black screen and then it takes me to the login. Is this normal ?

---

### Post by monkeybrain20122 on 2017-06-09
It is normal. "Silent boot" when you have only Ubuntu (instead of dualboot or multiboot) is a feature, not a bug. :) To see the grub menu press the esc key (some people say the shift key but esc works for me) when boot. If you want it to show the grub screen by default edit /etc/default/grub to comment out the grub_hidden line as [here]("https://askubuntu.com/questions/775437/how-to-get-to-the-grub-menu-at-boot-time").

---

