---
title: "Grub error 5/21"
date: 2007-02-24
forum: General Help
---

### Post by MikeBrandman on 2007-02-24
Hello,
       Sorry if this post is kind of disjopinted, I'm frantically trying to peice everything together.
I installed got a 250gb external hard drive yesterday.  I tried installing ubuntu on it serveral times, but there was always an error during partition.  I went to the hard drives application and had it write 0's to all of it.  I'm not sure if that's actually reformating, but it worked.
So I installed ubuntu to all 250 gigs of it, but during a restart there was a problem with it ubuntu not loading so I went back into windows and wrote 0's to it all over again.  I just restarted my computer and now i have a grub 5 error when I have the external plugged in and a grub error 21 when it is unplugged.  I am only able to post this message through by booting from the ubuntu disk.  I cannot access windows at all.
      Any advice would be greatly appreciated.

---

### Post by MikeBrandman on 2007-02-24
I just saw a previous forum post about this.  It said to run fixmbr after booting from the windows CD.  When and where do I do this?  I am such a noob...

---

### Post by MikeBrandman on 2007-02-24
Got it.  This has to be the lamest thread ever.  Sorry for wasting your time and the servers space.

---

### Post by tgalati4 on 2007-02-24
Most large capacity drives need to be broken in before running reliably.  From your installs and wipes, I would say that your disk is ready to run.

Boot from the live cd.  Mount your external disk in a terminal:  For example:
sudo mount /dev/sda1 /media/sda1
sudo more /media/sda1/boot/grub/menu.lst

Make note of the title, root, kernel and initrd lines for windows and ubuntu.

Post that data here if possible, otherwise you will need to make changes to reflect your hardware.

Also examine your device mapping

sudo more  /media/sda1/boot/grub/device.map

Look at the manual pages for grub:

man grub-install

The next time you install you can make changes in grub interactively:

In the grub menu, hit esc.  You are now in interactive version.

Type help to get a list of commands.

Error 21 is a stage 2 error (can't find kernel)
I don't recall ever seeing error 5.

You need to tell grub where your kernel and initrd file is located.  This starts with the root (hd0,0) command.  You will use the value shown in device.map and it many not be hd0,0.

Once that is done, they type in kernel /boot/vmlinuz (tab) and autocompletion will find your kernel.
You can do the same with initrd:  initrd /boot/initrd (tab)
boot

Hopefully it will boot properly.

To save these changes you will have to edit /boot/grub/menu.lst.

Because the grub menu files reside on the external drive, you will have to leave it plugged in when you boot.

Good luck.

---

