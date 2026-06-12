---
title: "Recovering GRUB"
date: 2008-05-17
forum: General Help
---

### Post by lastjuan on 2008-05-17
Hi all:

I'm a a very neofite Linux User so please had a little patience with me.

After I had installed Windows XP SP3, the GRUB is not loading (also I had a message that says "NTDLR is missing
Ctrl+Alt+Supr to Restart" ). It's possible in this circunstance to recover the GRUB. How? I'm accessing my laptop the Ubuntu Disc as a Live CD. As it stands right now, I couldn't use neither of the two OS. Any help will be appreciated.

Thanks

---

### Post by empthollow on 2008-05-17
You have to boot the live cd and open a terminal, then type:
```
sudo grub
```
you will get a grub command prompt, then type:
```
find /boot/grub/menu.lst 
```
it will list something like
```
(hd0,1)
```
grub starts counting at 0 always.  The hd0 will be the physical disk and the 1 refers to the 2nd partition. Anyway...Type:
```
root (hd0,1)
```
this tells grub where to look for it's config files, now type:
```
setup (hd0)
```
This assumes you have one hard drive and that the find command returned it as (hd0), now type:
```
sudo quit
```
this will exit the grub shell.  the final step - which may not be necessary - is to update the menu.lst file to contain all os's.  This should do the trick.
```
sudo update-grub
```
now reboot and you should be good to go.

---

### Post by lastjuan on 2008-05-18
Thanks, it had solved my Linux trouble. You had no idea of how grateful I'm.:):):):)

---

### Post by empthollow on 2008-05-18
glad to hear it :)

---

