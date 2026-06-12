---
title: "[SOLVED] startupmanager broke tty"
date: 2007-10-19
forum: General Help
---

### Post by Absorbed on 2007-10-19
I installed startupmanager in Gutsy and changed the resolution and and colour depth. Everything is working fine except tty1-6. If I ctrl+alt+f1 there isn't a prompt, only a blinking cursor in the top left. I can ctrl+alt+f7 back to gnome.

Any ideas?

---

### Post by Absorbed on 2007-10-19
I removed vga=792 in /boot/grub/menu.lst and now it works. I'm sure why it works, but it does.

---

### Post by chrisccoulson on 2007-10-19
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910) [br].[/br] ---------------------------- [br].[/br] [br].[/br]

---

### Post by Absorbed on 2007-10-19
Thanks. I think that's it.

---

### Post by Can+~ on 2007-11-05
THANK YOU. I had this same issue with boot-up manager.

:guitar:

---

### Post by watsoncj on 2007-11-22
I was experiencing the same behavior except X was on ALT+F9. My virtual terminals cam back after removing vga=794 from menu.lst.

---

### Post by fela on 2008-03-20
I have this problem aswell :S

Is the solution to just delete/comment out the whole of vga=xxx or replace it with a different number? :) if it works...

---

### Post by Absorbed on 2008-03-31
> **fela said:**
> I have this problem aswell :S

Is the solution to just delete/comment out the whole of vga=xxx or replace it with a different number? :) if it works...

The solution for me was to remove the "vga=xxx".

Edit: I've just installed Hardy, and there is no longer any problem. 1024x768 tty's! :D

---

