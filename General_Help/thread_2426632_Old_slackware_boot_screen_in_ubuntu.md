---
title: "Old slackware boot screen in ubuntu"
date: 2019-09-11
forum: General Help
---

### Post by cpdrenato on 2019-09-11
Dear all,


I would very much like to have this old school boot screen- verbose, with Tux icon. 

[https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Eight_copies_of_Tux_on_multi-core_processor.png/800px-Eight_copies_of_Tux_on_multi-core_processor.png](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Eight_copies_of_Tux_on_multi-core_processor.png/800px-Eight_copies_of_Tux_on_multi-core_processor.png)


[http://wiki.laptop.org/images/5/52/Bootscreen3.png](http://wiki.laptop.org/images/5/52/Bootscreen3.png)


Would anyone have a suggestion how to do it? I would really appreciate it.

I've been reading about framebuffer, but got nothing. Someone to help?

Best regards Renato Lucena

---

### Post by Adam_GUI on 2019-09-11
That looks like LiLo, the Linux Loader.
Here's an AskUbuntu article:  [https://askubuntu.com/questions/135426/what-is-lilo-and-its-uses]("https://askubuntu.com/questions/135426/what-is-lilo-and-its-uses")

It's considered legacy software.  Are you sure you want that?

If you just want a verbose boot, there are a lot of suggestions for GRUB2 here: [https://askubuntu.com/questions/39057/how-do-i-enable-verbose-mode-at-boot]("https://askubuntu.com/questions/39057/how-do-i-enable-verbose-mode-at-boot")

---

### Post by cpdrenato on 2019-09-12
No need for lilo, Gentoo Linux uses verbose boot with tux.

[https://linux-cdn.softpedia.com/screenshots/Gentoo-Linux_1.jpg](https://linux-cdn.softpedia.com/screenshots/Gentoo-Linux_1.jpg)
or
[https://ahelpme.com/public/media/tutorials/gentoo-minimal-installation-cd-amd64-x86_64-booting-uefi-step-5--c16a9193f7.png](https://ahelpme.com/public/media/tutorials/gentoo-minimal-installation-cd-amd64-x86_64-booting-uefi-step-5--c16a9193f7.png)
@cpdrenato

---

### Post by cpdrenato on 2019-09-19
> **Adam_GUI said:**
> That looks like LiLo, the Linux Loader.
Here's an AskUbuntu article:  [https://askubuntu.com/questions/135426/what-is-lilo-and-its-uses](https://askubuntu.com/questions/135426/what-is-lilo-and-its-uses)

It's considered legacy software.  Are you sure you want that?

If you just want a verbose boot, there are a lot of suggestions for GRUB2 here: [https://askubuntu.com/questions/39057/how-do-i-enable-verbose-mode-at-boot](https://askubuntu.com/questions/39057/how-do-i-enable-verbose-mode-at-boot)

No need for lilo, Gentoo Linux uses verbose boot with tux.

[https://linux-cdn.softpedia.com/scre...oo-Linux_1.jpg]("https://linux-cdn.softpedia.com/screenshots/Gentoo-Linux_1.jpg")
or
[https://ahelpme.com/public/media/tut...c16a9193f7.png]("https://ahelpme.com/public/media/tutorials/gentoo-minimal-installation-cd-amd64-x86_64-booting-uefi-step-5--c16a9193f7.png")
@cpdrenato

---

### Post by fragglebliss on 2019-09-19
All you gotta do is press ESC on the graphical boot loader and it will fallback to verbose. Saves screwing around with hacking GRUB configs and running the risk of screwing your entire boot if you don't know what you're doing.

---

