---
title: "Want to eliminate grub"
date: 2008-05-08
forum: General Help
---

### Post by jimroby on 2008-05-08
Put up a new install with half the disk given to Win2K and the remainder given to Ubuntu.Grub was automatically installed.Later decided to give the entire disk to Ubuntu,but Grub boot manager still comes up.I wiped the hd0 and then resized hd1.How do I uninstall Grub,or edit it's config.I have tried using the 'e'
option but still confused.By resizing the disk how does the system recognize that hd0 no longer exists,and make hd1 now into hd0.
Machine has a single hard disk,Ubuntu boots ok,but I no longer need the boot manager.I used gpart to reconfigure booting off the live CD. TKX

---

### Post by angry_johnnie on 2008-05-08
You still need the boot manager in order to boot your computer, you know...  So, you most likely don't want to remove GRUB.

If you don't want to see it, you can just hide it.

Open a terminal and type

```
gksu gedit /boot/grub/menu.lst
```

In that document, find this part:


```
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu
```


Uncomment hiddenmenu (remove the # sign).
And, also, change timeout to something lower.

---

