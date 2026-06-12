---
title: "Ubuntu, Windows 7 and SteamOS. DualBoot"
date: 2015-04-19
forum: General Help
---

### Post by freefaction1 on 2015-04-19
I used Grub Customizer to modify the order in the Grub Menu. Everything went fine.
Then I installed SteamOS on a third partition and the grub menu completely changed but cannot be modified by Grub Customizer anymore.

I looked inside the /boot/grub/grub.cfg file but got lost pretty fast. 
I want to modify the Grub Menu again, anybody has any ideas

Thx all
Jog.

P.S My first time using the Ubuntu Forum... not sure I'm doing it right (or in the right section)

---

### Post by Mark Phelps on 2015-04-20
Sorry, don't use Steam OS, so I can't provide any details.

But,what I can tell you is NOT to make changes to grub.cfg.  This file is automatically rewritten anytime a kernel update is applied -- thus, removing any changes you may have made to it.

If Steam OS has a forum, you might check with them to see what they suggest

---

### Post by verymadpip on 2015-04-20
Hi there.
I'd be tempted to reinstall Grub using your Ubuntu install medium.

I had some issues with SteamOS's implementation of Grub (long story),
so I installed Ubuntu & allowed its Grub to control my boot selection.
I've never used Grub Customizer so this is all I have really...

---

