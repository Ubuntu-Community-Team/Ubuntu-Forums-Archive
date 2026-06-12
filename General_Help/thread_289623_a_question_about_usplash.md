---
title: "a question about usplash"
date: 2006-10-31
forum: General Help
---

### Post by ynnhoj on 2006-10-31
so when my system is getting fired up, i see an ubuntu logo and a progress bar--they look nice--but that's all.  how can i make it more verbose?  y'know, typically you'd see read-outs of all things that are being done in the process of booting up..

so do i need to change a setting somewhere, or hit a certain key while it's booting up?  i've done some googling and searching on here, but i haven't really come up with anything. :-|

---

### Post by PriceChild on 2006-10-31
You're talking about "usplash" ;) - i've renamed your thread appropriately.

---

### Post by karlbowden on 2006-10-31
Assuming you are using grub.
First open up /boot/grub/menu.lst in your favourite editor with root priv's.
```

gksudo gedit /boot/grub/menu.lst
```

Find the following paragraph:

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791
# defoptions=splash quiet
```

And remove the 'quiet' from the last line like so:

```
# defoptions=splash quiet
```

Then update grub:

```
sudo update-grub
```

and reboot.

---

### Post by ynnhoj on 2006-10-31
> **PriceChild said:**
> You're talking about "usplash" ;) - i've renamed your thread appropriately.

it's funny; i looked up this thread just now, and i thought.. "why on earth did i type 'usplash' in the name???"  but now i know, thank you.

and thanks for the answer, karlbowden.  i'll do that now.

---

