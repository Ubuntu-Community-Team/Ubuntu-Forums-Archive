---
title: "Can't boot into Ubuntu"
date: 2023-08-06
forum: General Help
---

### Post by chris-burmajster on 2023-08-06
Hello Friends,

I can't boot into Ubuntu. I have two Ubuntu computers and both do something that leaves me with a text login. I login and it provides a text based computer. Is there anything I can type to bring it back to Ubuntu full strength? I have tried pressing Escape during boot but that leads me how ever I do it to the login screen. Can somebody please help me?

Chris

---

### Post by ajgreeny on 2023-08-06
Might be related to this nasty bug
[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2030262](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/2030262)

---

### Post by iamtheeggman2 on 2023-08-06
I just had the same issue yesterdday, I updated and it stopped the desktop from loading, I reinstalled did updates again and had the same issue. I have however just discovered if I choose to boot up not using the kernel 6.2 but use the previous one instead, it booted into the desktop. I am however in need of some help to make the previous kernel the default one to boot up on until they fix it, does anyone know how to do this please? Thanks in advance.

EDIT: I found this and it removed the new kernel.
[https://askubuntu.com/questions/1338398/how-do-i-remove-newest-kernel](https://askubuntu.com/questions/1338398/how-do-i-remove-newest-kernel)

---

### Post by chris-burmajster on 2023-08-08
Hello Friends,

Well, it's a bug. So I will have to put Ubuntu back on. I have backups so it won't be too bad. Thanks for letting me know that it's a bug. hope it'll be fixed soon.

Chris

---

### Post by iamtheeggman2 on 2023-08-13
It seems this bug still exists, does anyone know if I choose the partial upgrade option in the updates if this can make things any worse or should I just avoid updates for a few more weeks? My solution of reverting to a previous kernel works still in regards to booting into the MATE desktop. I find it strange that in itself helped me boot into the desktop but the instructions on the remove newest kernel I read said kernel upgrades would not be part of the future updates, so it seems there is more than one bug in my opinion. I am using proprietary nvidi5 535 drivers. Thanks in advance.

---

