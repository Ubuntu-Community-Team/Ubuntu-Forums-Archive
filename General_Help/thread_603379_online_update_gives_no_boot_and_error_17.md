---
title: "online update gives no boot and error 17"
date: 2007-11-05
forum: General Help
---

### Post by kwalters on 2007-11-05
NB I am talking about the online regular "updates" to an existing 7.04 installtion, NOT and upgrade to 7.10

For the past several months, every time I have accepted an online update, my Ubuntu has then refused to boot, quoting error 17, unable to mount selected partition.

This caused me no end of grief until I discovered that something in the update process was making changes to my menu.lst file in /boot/grub.   My Ubuntu choices all require the use of (hd0,0); the update process somehow changes that to (hd0,3)  [this is a linux swap partition]

I edit the file back to the correct version using  rescue CD, and everything is OK; but it is quite irritation when it keeps happening

KW

---

### Post by Herman on 2007-11-05
Hello kwalters,
Have you checked your line for 'groot', in your "DEBIAN AUTOMAGIC KERNELS LIST", in your /boot/grub/menu.lst file? :)
[groot=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot") (grub root device)

I'll bet it says '(hd0,3)' for some reason. Maybe your partition numbers have changed since you first installed Ubuntu somehow, or you restored this operating system from a partimage backup or something like that? (And it used to have a different partition number once)?

The DEBIAN AUTOMAGIC KERNELS list, in the mid to lower section of the /boot/grub/menu.lst file is important for helping the update-grub script make a new menu.lst file when we are given a new kernel in an update.

Probably you need to edit that groot line to (hd0,0) to make sure it will be programmed right from now on.
That should fix it. :)

Regards, Herman  :)

---

