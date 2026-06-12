---
title: "After an update to Kernel 6.1 my Logitech mouse has high-resolution scrolling enabled"
date: 2023-09-06
forum: General Help
---

### Post by earthmapspictures on 2023-09-06
Hello reader,

I have recently (2 months ago) updated to Kernel 6.1, my mouse has been acting weird since then. I have started research on the subject and I have now found a reason for it. 

You can check my older post about it here (includes more details about my research): [https://linustechtips.com/topic/1529515-gnome-smooth-scrolling-has-turned-on-after-an-update-how-to-turn-off/#comment-16125991](https://linustechtips.com/topic/1529515-gnome-smooth-scrolling-has-turned-on-after-an-update-how-to-turn-off/#comment-16125991)

So sum it up here, I have not been able to turn it off without referring to Wayland (currently on X11) or doing this thing ([https://bbs.archlinux.org/viewtopic.php?pid=2091247#p2091247](https://bbs.archlinux.org/viewtopic.php?pid=2091247#p2091247)), after which breaks it again after a restart. This seems to be a problem on the new kernel version, as it is persent on Arch too. But I suspect me to be facing a problem with X11 too, as I think it is where you also save the configuration files for the mice. I can double down on this as I did not encounter the issue on Wayland, but Wayland will not be an option because I have an nVidia GPU.

Does anyone have any way that I can solve this?

Please do not hesitate to ask me about the situation, I will be more than happy to help.

Thanks for reading!

---

