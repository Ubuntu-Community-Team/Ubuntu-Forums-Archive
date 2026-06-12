---
title: "Problem booting after updating to 2.6.20-16-generic"
date: 2007-06-25
forum: General Help
---

### Post by oska on 2007-06-25
After updating to linux kernel version 2.6.20-16-generic my system hangs. I see the grub menu and then after the default (the latest kernel version) is automatically chosen the system hangs with just a blank screen showing with a flashing cursor.

This happened on the very first boot after the kernel update.

I have tried selecting the previous kernel versions in the grub menu but they also now result in hanging.

The disk I am booting from is one I did a clean install of feisty on. It has one partition formatted with jfs and one swap partition.

I have another disk in my computer with my old install of edgy on it. I can select to boot from that on the grub menu and that boots up ok. From that bootup I have run fsck.jfs on the other disk and it is coming up clean.

Is anyone able to give me a lead into what checks I should run or what  tools I should try to fix the problem? Thanks in advance.

---

### Post by merlinus on 2007-06-25
It probably messed up the grub root.

Press e when the grub menu appears, and see what it says.  Should be something like (hd0,3).  Unless you know which partition ubuntu resides on, you will probably have to change the last number a few times until it works.

-merlin

---

### Post by oska on 2007-06-25
Thanks for your reply Merlin.

I went in and had a look at the scripts in grub for both the non-working menu selection with feisty on my new disk and the still working menu selection with edgy on my old disk.

I've copied them below:

First the working boot into edgy on /dev/hdc1

[FONT="Courier New"]root (hd1,0)
kernel /boot/vmlinuz-2.6.15-28.386 root=/dev/hdc1 ro quiet splash
initrd /boot/initrd.img-2.6.15-28-386
savedefault
boot[/FONT]

Second, the not-working boot into feisty on /dev/hda1

[FONT="Courier New"]root (hd0,0)
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=4f20[...] ro quiet splash
initrd /boot/initrd.img-2.6.20-16-generic
quiet
savedefault[/FONT]

From my understanding the hd0,0 does correctly match the /dev/hda1 location?

However I do note two differences in the non-working feisty menu selection.

Firstly, in the kernel command, root is specified as a UUID number (which I have abbreviated above) rather than /dev/hda1.

Secondly, that the boot command is missing.

Which of these two do you think is the problem? Or both? I will go and read up on how to edit and keep the changes to the script because when I was trying to do this just now I wasn't having much luck.

Thanks.

---

### Post by merlinus on 2007-06-25
You can also try this in a terminal:

```

sudo grub
find /boot/grub/stage1
quit

```

This will return something like (hdx,x), which you can then edit into grub from the startup menu.

If running from the live cd, you will probably need to mount your ubuntu partition.

-merlin

---

### Post by oska on 2007-06-25
Thanks again for replying merlin.

I did something similar to what you are saying after having a look in the grub manual. I found that in grub you can type root( and then by using tab completion it will show you what is available. It showed me hd0 and hd1. I selected 0 for the first disk and then tabbed again to show partitions. It correctly showed me the single partition on my first disk.

So hd(0,0) is right I think.

However, an interesting error message appeared when I did this command. It was Error 18: Selected cylinder exceeds maximum supported by BIOS.

My computer is an old Pentium 3. I'm thinking that the actual problem is that I might be running into BIOS limits. Yuck. Will have to look at resizing the JFS partition - not sure how to do this but will now go and investigate.

---

