---
title: "Raid setup: Grub not updated with new kernels"
date: 2008-06-30
forum: General Help
---

### Post by bogoliubov on 2008-06-30
Hello. I use a raid setup (mirror) with two disks of the same size. I just realized that in the /boot/ folder the newest kernel is 2.6.24-19, but Grub only shows 2.6.24-16! How can I fix this? And how do I set up grub so these changes are reflected on Grub on both disks?

---

### Post by caljohnsmith on 2008-06-30
I'm not exactly familiar with your setup, but wouldn't it be as simple as updating your /boot/grub/menu.lst with entries for the new kernels? Usually when you install a new kernel through Synaptic it prompts you what you want to do with your menu.lst (how you want to update it). If you need specific help with modifying your menu.lst let me know, but it's usually straightforward to copy an existing entry in menu.lst that works and just modify it with the new kernel numbers.

---

### Post by bogoliubov on 2008-06-30
Yeah, you're right. Actually, it turned out I did choose not to let synaptic install a new menu.lst, since there is a trouble with my config. I need to have "irqpoll" as a flag for the kernel. Therefore I need to update it myself...

Thanks for the help though

---

