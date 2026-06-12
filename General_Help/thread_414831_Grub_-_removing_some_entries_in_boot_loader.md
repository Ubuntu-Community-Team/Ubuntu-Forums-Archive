---
title: "Grub - removing some entries in boot loader?"
date: 2007-04-20
forum: General Help
---

### Post by StevenX on 2007-04-20
After upgrading to Feisty I now have multiple entries for Ubuntu in my GRUB boot loader.
```
title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1f875bd5-5e6b-487e-8e9b-bb51de1b5775 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1f875bd5-5e6b-487e-8e9b-bb51de1b5775 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, kernel 2.6.17-11-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=1f875bd5-5e6b-487e-8e9b-bb51de1b5775 ro quiet splash
initrd		/boot/initrd.img-2.6.17-11-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-11-generic root=UUID=1f875bd5-5e6b-487e-8e9b-bb51de1b5775 ro single
initrd		/boot/initrd.img-2.6.17-11-generic

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=1f875bd5-5e6b-487e-8e9b-bb51de1b5775 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=UUID=1f875bd5-5e6b-487e-8e9b-bb51de1b5775 ro single
initrd		/boot/initrd.img-2.6.17-10-generic

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin
```
These are all the systems which show up on loading, as well as WInXP at the bottom under Other Operating Systems.
How can I remove all of these entries except the top two and memtest86+ (which I assume is important?) - surely they're not all necessary? Do I just delete these entries, or change something in the settings above?
Thanks in advance.

---

### Post by Compyx on 2007-04-20
I just delete the entries with gvim, but there should be a cleaner, more 'ubuntu' way of doing it. If I remember correctly you should remove all occurences of old kernels and then run grub-install.

Something like:
```
sudo apt-get autoclean
sudo grub-install
```

However, it would be best to wait if someone who actually has done this before replies to this thread :)

---

### Post by rich.bradshaw on 2007-04-20
I just delete them all except the newest one. I even delete recoevery and memory test.

Remember to set default at the top to which ever one you want. There are a couple of lines which ask howmany kernels to keep in the menu and whethere or not to create a memtest entry. You can change the values of these safely.

sudo apt-get autoclean

will remove all installed packages and old kernels - again complelty safe if the kernel you are in now works.

---

### Post by Zdravko on 2007-04-20
I use Start-up Manager. It is in the repos. Very nice application for GRUB editing.

---

