---
title: "ctrl-alt-f1 crash with blank screen"
date: 2008-05-09
forum: General Help
---

### Post by jroper73 on 2008-05-09
When I hit Ctrl-Alt-F1 my system crashes with a blank screen.

At times when the computer has been idle for a while, I will get the same blank screen crash. I think it has something to do with the screen saver or perhaps system standby. But I've seen both work, so I am unsure what it is.

I have tried several things in various forums, including modifying /etc/initramfs-tools/Modules to include fbcon and vesafb and /etc/modprobe.d to comment out the blacklist of vesafb. But this did not work.

I am rather rusty with linux so please be detailed with any suggestions. 

I am using:
Ubuntu 8.04
Compaq Presario V6000 Laptop
nvidia graphics card

Thank you
James Roper

---

### Post by webaake on 2008-05-09
I'm not sure I understand exactly what you mean, but I had the same problems too; when trying ctrl-alt-F1 the screen went black.  In my case it didn't really crash though, I could use it 'blindly'.

But I solved it by adding video=vesafb at the and of kernel start parameters in /boot/grub/menu.lst.
I also did activate fbcon in modules and in initramfs, same as you.

By the way, I'm not sure vesafb needs to be activated as module since it seems to be compiled into the kernel in 8.04.

Hope this helps! Without a terminal you could be lost.....

---

### Post by fbnaia on 2008-05-09
I had a similar issue before, was getting only a black / blank screen on ctrl-alt-f1. I played with a program called "startup manager" (installable thru add/remove) that added vga=### settings to my grub menu.lst. 

I had to manually edit the menu.lst file to get ctrl-alt-f1 working correctly again. 

I actually removed the vga settings completely from the kernel line on menu.lst and that resolved the issue for me.

---

### Post by jroper73 on 2008-05-09
video=vesafb in the kernel portion of the grub entry, with a reboot, did not work. :(

Since there was no VGA= line in my menu.lst, there is nothing for me to remove.

Still need help, but thank you for the suggestions.

James

---

### Post by webaake on 2008-05-09
This is how my first kernel entry looks like in /boot/grub/menu.lst

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=4653cc47-c2cd-4837-be00-5a8cac896ecc ro video=vesafb vga=0x311
initrd		/boot/initrd.img-2.6.24-16-generic

I do have a vga parameter; 0x311 and it means 680x480 16 bit color, which should be a safe bet to begin with.

Concerning removing the vga= option; it seems some fix their problems by removing it, some by adding it. You could try both approaches.

When it comes to grub there seems to be a bit voodoo involved.....

---

