---
title: "Tried to downgrade from GRUB2 to GRUB but can't boot into Ubuntu now"
date: 2013-03-21
forum: General Help
---

### Post by Juahah on 2013-03-21
So I just did a clean install of windows 7 ultimate and installed ubuntu 12.10 beside it. I kept the windows bootloader in the mbr at the advice if my tutorial (i used easyBCD to enable an option for grub2) and installed grub2 to the /boot partition that I made for sda5. If it matters, I set / as sda6, /home as sda7 and swap as sda8. I wanted to encrypt my windows partition with truecrypt, and I read to downgrade from grub2 to grub first, so I did (or at least attempted to). the code I used to replace grub2 with grub is attached.[ATTACH=CONFIG]240394[/ATTACH]

However, it leads me into a command line titled "GNU GRUB version 2.00-7ubuntu11". I don't know why it still says version 2. Anyways, I can't even boot into Ubuntu now. From what I understand of grub (a very limited understanding admittedly), I need to use the root, kernel, and boot command to boot up ubuntu. But the problem is that root and kernel don't even exist as commands in the grub terminal. I pressed tab to list all the commands and they weren't among them. Typing them into the terminal yields no result. How do I get into ubuntu now?

---

