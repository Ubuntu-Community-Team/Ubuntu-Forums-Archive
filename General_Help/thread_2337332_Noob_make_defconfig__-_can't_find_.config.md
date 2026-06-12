---
title: "Noob: make defconfig  - can't find .config"
date: 2016-09-16
forum: General Help
---

### Post by dh29 on 2016-09-16
OK, this is my 1st dabble with linux. I've read a few articles and thought I'd take a look at the linux kernel build system.

I've downloaded and installed Ubuntu 16.04 LTS within VirtualBox. I've then downloaded the Xenial source files as a starting point to 'play' with something.

Upon trying to generate a default .config file I'm stuck!! I know I could just copy the x86_64_defconfig from /arch/x86/configs but I thought I'd try and generate it.

I've issued the command:
[INDENT][COLOR=#ff0000]dh29@dh29-VirtualBox:~/linux/ubuntu-xenial$ make defconfig[/COLOR][/INDENT]

and I get the following back,
[INDENT][COLOR=#ff0000]*** Default configuration is based on ‘x86_64_defconfig’
#
# configuration written to .config
#[/COLOR][/INDENT]
 I look for the .config file by listing the folder contents,[INDENT][COLOR=#ff0000]dh29@dh29-VirtualBox:~/linux/ubuntu-xenial$ ls[/COLOR][/INDENT]
but the file .config is not there.

What am I missing?

---

### Post by jeremy31 on 2016-09-16
.config is a hidden file, use CTRL + h to show hidden files

---

### Post by howefield on 2016-09-16
Thread moved to the "*General Help*" forum.

Also in addition to Ctrl + H showing hidden files/folders in the gui, you could use the terminal command..

```
la -al
```

---

### Post by dh29 on 2016-09-18
:D

Never thought of that - seems obvious now - but everything is once you know!!

Many thanks to **Jeremy31** & **howefield** for taking the trouble to post - this was driving me mad!

---

### Post by howefield on 2016-09-18
> **dh29 said:**
> ...but everything is once you know!!

Absolutely :)

---

