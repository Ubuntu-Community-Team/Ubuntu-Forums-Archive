---
title: "make grub invisible"
date: 2007-05-28
forum: General Help
---

### Post by jeff0101 on 2007-05-28
I no how to hide the menu and have done that, i want to make the 2 lines before that disappear too. It says loading grub.. before the menu is displayed. I don't want it obvious that my pc is a dual boot at all. please advise.

---

### Post by Kobalt on 2007-05-28
Try setting *timeout=0* in /boot/grub/menu.lst.

---

### Post by Slim Odds on 2007-05-28
> **Kobalt said:**
> Try setting *timeout=0* in /boot/grub/menu.lst.

It'd be a little hard to **dual boot** then, don't ya think?

---

### Post by Kobalt on 2007-05-28
> **jeff0101 said:**
> I no how to hide the menu and have done that ... I don't want it obvious that my pc is a dual boot at all. please advise.
Isn't this what he wants...

---

### Post by m.musashi on 2007-05-28
> **jeff0101 said:**
> I no how to hide the menu and have done that, i want to make the 2 lines before that disappear too. It says loading grub.. before the menu is displayed. I don't want it obvious that my pc is a dual boot at all. please advise.

Do you still want to dual boot? Or do you want to dual boot when YOU want to but for everyone else it just boots the default OS? Rather than getting rid of grub, why not just edit menu.lst to only show one option. I did that once. Left in the 3 lines for ubuntu (regular, recovery, mem test) and nothing else. When someone boots they only have once choice - ubuntu (or they can run a mem test:)). Keep a backup of menu.lst in case you want to go back.

---

### Post by strabes on 2007-05-28
You could set the timeout to 1. That way, other people using your computer wouldn't have time to read the menu and select windows. But, because you know your scheme, you can select windows quickly by simply holding the down arrow as the grub menu is loading.

---

