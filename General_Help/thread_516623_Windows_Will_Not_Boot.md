---
title: "Windows Will Not Boot"
date: 2007-08-03
forum: General Help
---

### Post by Phalax on 2007-08-03
This problem is weird and I can not explain it. First time I heard about Wubi I was excited to use it so I installed Kubuntu, but did not like it so I uninstalled it and installed Ubuntu. Ubuntu and Winows was working fine before I went on vacation with relatives for couple days. I come home try booting up into windows and it gives me a blank screen and does not boot? If I restart and when I get to the boot screen and boot into Ubuntu it works fine! Before I left I updated ubuntu, and installed Beryl. I know windows was working before I left cause I was playing couple games on it. It is so frustrating trying to solve the problem and was wondering what steps I should take to try and solve it? I tryed repairing, booting up in safe mode, debugging mode and they don't work. 

I am able to access the Host drive and copy over files from my windows drive and everything. I was wondering if by going into my Host drive then to the wubi folder "C:\Wubi" and if I uninstall Wubi by the "wubi-unistall.exe" It will work and will let me boot up into WIndows Media Center? I know I need wine to do it.

 Thank you guys very much.

---

### Post by tuxcantfly on 2007-08-03
> I am able to access the Host drive and copy over files from my windows drive and everything. I was wondering if by going into my Host drive then to the wubi folder "C:\Wubi" and if I uninstall Wubi by the "wubi-unistall.exe" It will work and will let me boot up into WIndows Media Center? I know I need wine to do it.

Using wine to try to uninstall Wubi won't help you at all. First of all, wine uses its own configuration directory, with its own registry and everything, and second of all, even if you do adjust your wine settings to get it to use the Windows drive as wine's C: drive, all it'll do is prevent you from booting into Ubuntu (since it'll just remove the ubuntu entry from boot.ini and delete your Ubuntu install), and you'll be even more screwed.

I'd say the best bet would be to try starting windows, and as soon as you start the entry, mash the F8 button, and that'll let you get into the "safe mode", where you can do diagnosis of your problem.

Another thing that comes to mind is that your Windows partition might have a couple of filesystem errors; you might want to boot up an XP recovery cd, press R to get into recovery mode, then use the command

```
chkdsk /r C:
```

And hopefully, that'll correct any errors on your Windows partition and let you boot it properly.

---

