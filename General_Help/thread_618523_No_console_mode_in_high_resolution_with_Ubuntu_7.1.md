---
title: "No console mode in high resolution with Ubuntu 7.10"
date: 2007-11-20
forum: General Help
---

### Post by Shyron on 2007-11-20
Hello, 

Since I have installed Ubuntu 7.10, I can't have a high resolution in console mode.

For example, if I put vga=791 in the menu.lst, I have got a black screen when I tape CTRL+ALT+Fx.

If I don't change anything in the menu.lst, it works but I have got a 640*480 resolution.

What can I do ?

With the others Ubuntu versions, 6.10 or 7.04 for example I can do that but not with the 7.10 version.

---

### Post by zach12 on 2007-11-20
it's ctrl alt f1 for console

---

### Post by bingoUV on 2007-11-20
> **Shyron said:**
> Hello, 

Since I have installed Ubuntu 7.10, I can't have a high resolution in console mode.

For example, if I put vga=791 in the menu.lst, I have got a black screen when I tape CTRL+ALT+Fx.

If I don't change anything in the menu.lst, it works but I have got a 640*480 resolution.

What can I do ?

With the others Ubuntu versions, 6.10 or 7.04 for example I can do that but not with the 7.10 version.

Well, I also get a black screen but there is some text written in white that asks me for login and password. So, I say it works for me. Is there no such white text for you?

If it is totally black without any white text, are you sure you need 791, and not some other number?

---

### Post by Shyron on 2007-11-21
Finally I find the solution :

Add vesafb and fbcon in /etc/initramfs-tools/modules
then : update-initramfs -u
then in : /etc/modprobe.d/blacklist-framebuffer , comment vesafb
Finally in /etc/modules, add vesafb

---

### Post by piotrwoj on 2007-11-21
> **Shyron said:**
> Finally I find the solution :

Add vesafb and fbcon in /etc/initramfs-tools/modules
then : update-initramfs -u
then in : /etc/modprobe.d/blacklist-framebuffer , uncomment vesafb
Finally in /etc/modules, add vesafb
Thanx!!!!!!!
This is work me :))))
-------------------------
[Meble dla Dzieci](http://www.spok.pl/)

---

### Post by Wooksta on 2007-11-23
*Bump*

Perfect, that worked for me as well

Thanks!

---

### Post by monkeyking on 2007-12-22
sitting on a lenovo 3000 n200 laptop, and it doesn't work for me,
any ideas.?

---

### Post by Shyron on 2007-12-23
I have just seen I made a mistake in my explication :

Instead of uncomment vesafb in /etc/modprobe.d/blacklist you must comment vesafb.

Perhaps it will be good now four you.

---

### Post by Masher23 on 2008-03-23
@ Shyron

Thank you very much for this ! That was the last problem i had with my new Kubuntu 7.10. I have been trying to get highres working in the console for some days. I followed alot of tips on different threads but nothing has helped so for. Your tip did it.

This is the first time i post on this forum, i just switched from vista to kubuntu and i really wanted to say thanx to everyone who posts tips and help people here. This forum was very helpful in getting started with linux so far.

- Masher

---

