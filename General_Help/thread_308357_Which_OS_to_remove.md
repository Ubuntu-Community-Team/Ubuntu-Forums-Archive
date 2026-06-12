---
title: "Which OS to remove"
date: 2006-11-27
forum: General Help
---

### Post by Russty of Oz on 2006-11-27
Hi,

I have done this sort of thing before but back them I had some Linux Headers that did not have the Ubuntu logo next to them so it was easy to decide which ones to remove.

I now have 3 Linux options at boot up time and wonder if it is safe to remove any of them?  See the attachment and let me know if I can safely remove any of them.  I want to put Feisty on a separate partition soon so I don't want too many there to confuse the matter.

Russty.

---

### Post by dlehman on 2006-11-27
Well I don't know about removing those packages they all look current 2.6.17-10 if you want to limit your choice at boot comment out the title line in your grub menu.lst file

backup first
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

```
edit menu file
```
gksu gedit /boot/grub/menu.lst
```

then find the title lines of the entries you no longer use 2.16 kernels etc by place the # sign at the beginning of the line

---

### Post by Russty of Oz on 2006-11-27
OK, thanks I will try that. :) 

Russty.

---

