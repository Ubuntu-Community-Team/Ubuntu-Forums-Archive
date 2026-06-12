---
title: "[SOLVED] Console Font Size"
date: 2008-06-26
forum: General Help
---

### Post by Capheind on 2008-06-26
I've been away from the faith for a bit and have forgotten one or two things. First amung those is how to change the font size in the console (As in ALT+Fn). The Ubuntu Default is huge and ungainly. Any thoughts on how to fix that?

---

### Post by ryanhaigh on 2008-06-26
I believe what you need to go is add something like VGA=791 to the grub boot option associated with the kernel you are booting. This has alternate modes you could use: [http://www.mepis.org/node/2992](http://www.mepis.org/node/2992)

---

### Post by jw5801 on 2008-06-26
Try adding a vga=791 or similar setting to your kernel boot options in /boot/grub/menu.lst and then reboot.

```
gksudo gedit /boot/grub/menu.lst
```
Then look for this section:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash
```
And change it to:
```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791
```
Now save and close gedit, then run:
```
sudo update-grub
```
And reboot.

The only reason I suggest using 'update-grub' and editing the defoptions is so that any new kernels that are installed will be autoconfigured with the option. You could simply append it to the kernel entry at the bottom of the file, if you so chose.

---

### Post by Capheind on 2008-06-27
that did it, thanks.

---

