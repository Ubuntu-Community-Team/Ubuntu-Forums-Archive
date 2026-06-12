---
title: "Getting Grub quieter"
date: 2007-11-04
forum: General Help
---

### Post by guzzi333 on 2007-11-04
On my own laptop I'm running ubuntu since the warty warthog (and upgraded always to the latest version by upgrading via update-manager) and my GRUB menu looks more or less like this

[IMG]http://yekubuntu.free.fr/warty/images/grub.png[/IMG]

If I make the selection I see stuff like

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=42178367-d6be-4e24-a453-ead057e02dc5 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet
savedefault

scrolling over the screen

On another laptop I install edgy eft. There the grub menu does not show the version info and also does not show the GRUB commands when I made my selction but says something like "Starting ...."

I can't spot any difference in the menu.lst files. How can I get grub to be quieter?

---

### Post by troyer81 on 2007-11-09
Hmmm....I don't know why you don't see any difference between the two files, but the option that you need turned on in the /boot/grub/menu.lst file is the "hiddenmenu" option.  My file has a section that looks similar to this:

```
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```If your file still has the # sign in front of the hiddenmenu line, then the option is "commented out" and doesn't turn on.  Hopefully that works.  Otherwise I would start looking at potential conflicting options, such as the "timeout" setting.  If you want all of the details, you can always read the manual with:

```
man grub
```

---

