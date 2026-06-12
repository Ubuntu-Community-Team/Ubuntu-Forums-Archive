---
title: "Boot to VGA Console"
date: 2005-05-16
forum: General Help
---

### Post by hammett111 on 2005-05-16
Hi, I wanna install nVidia drivers and boot to VGA console, not X-server. I know how to shut down x-server to do the install but how do I boot to VGA console and not X server?

---

### Post by Laemel on 2005-05-16
[QUOTE=hammett111]Hi, I wanna install nVidia drivers and boot to VGA console, not X-server. I know how to shut down x-server to do the install but how do I boot to VGA console and not X server?[/QUOTE]
 Open up a prompt and type ```
$ sudo rcconf
``` If it says "command not found", you'll need to install rcconf using apt-get or synaptic.  Once you're in rcconf, deselect gdm (or xdm or kdm, whichever one you have) and hit Enter.  Then reboot and you should just get a text login.

Now, if you want to have a nice high-res console instead of the 320x240 piece of crap that Ubuntu has by default, you'll have to edit your GRUB config.  So, type```
$ nano -w /boot/grub/menu.lst
``` at a prompt and then scroll down until you find the section that looks something like ```
title           Ubuntu Linux 5.04
root            (hd0,1)
kernel          /vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash vga=0x318 video=mtrr,ywrap
initrd          /initrd.img-2.6.10-5-386
savedefault
boot
``` and add on the "vga" and "video" segments that you see there.  For a list of all the vga modes, check out [this](http://techpatterns.com/forums/about342.html) (The hexadecimal ones at the bottom are what you want.)

---

### Post by hammett111 on 2005-05-18
Sorry mate this is all I get in the grub menu.lst

title           Ubuntu, kernel 2.6.10-5-amd64-generic Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro console=tty0 quiet splash
initrd          /boot/initrd.img
savedefault
boot


NO VGA or Video options!!

---

### Post by Laemel on 2005-05-18
[QUOTE=hammett111]Sorry mate this is all I get in the grub menu.lst

title           Ubuntu, kernel 2.6.10-5-amd64-generic Default
root            (hd0,0)
kernel          /boot/vmlinuz root=/dev/sda1 ro console=tty0 quiet splash
initrd          /boot/initrd.img
savedefault
boot


NO VGA or Video options!![/QUOTE]
 Add them :)

Just tack on vga=something and video=mtrr,ywrap to the end of the kernel line. Also, I noticed you have the console option set, which I don't, so if adding the video stuff doesn't work you can try deleting console=tty0 and see if that does it.

---

### Post by hammett111 on 2005-05-18
Any hint on how to change the uid on files? I have accidentally changed the uid 0 (root) on my sudoers file to uid 1000 (me) and now I cant access sudo commands or root until I fix it.

Cheers

---

### Post by Laemel on 2005-05-19
[QUOTE=hammett111]Any hint on how to change the uid on files? I have accidentally changed the uid 0 (root) on my sudoers file to uid 1000 (me) and now I cant access sudo commands or root until I fix it.

Cheers[/QUOTE]
 chown is the program you use to change the ownership of a file.  Simple usage is "chown root:root filename" or "chown hammett:users filename"

---

