---
title: "Bootable USB Drive to boot a LiveCD"
date: 2007-04-10
forum: General Help
---

### Post by ocho on 2007-04-10
I am in a conundrum. I have a PC I want to boot an Ubuntu LiveCD on, but it only has the option to boot flash drives, I cannot even boot floppies. 

Is there any way to install GRUB or some type of boot manager onto my flash drive to allow me to boot from CD? My flash drive is not nearly big enough to hold the LiveCD, so I don't want to boot Ubuntu from my flash drive.

Thanks for any help.

---

### Post by gingin on 2007-04-10
I do assume as you have  PC.
Would be strange wonder around with UBUNTU  live cd in your hands with out having pc.

But what is a solution to you problem ?
Make sure as you can boot from cd. You must adjust that in Bios. Boot cd it not a floppy or flash drive. You must have CD or DVD rom for booting CD.

---

### Post by ocho on 2007-04-10
I don't think I made my situation very clear...At my school all PCs' bioses are set to disallow booting from CD's, and they do have CD drives, and floppies. They are, however, able to boot from a USB flash drive. 

What I want to do is install some sort of boot manager on my flash drive to allow me to boot from the CD. I've searched all over for a utility able to do this, finding none.

And don't worry, my teacher has actually encouraged me to boot Linux on these computers, so I'm not breaking any rules.

---

### Post by ocho on 2007-04-10
Bump. Anyone have any ideas?

So far, I've tried using a DOS based GRUB to boot to the CD, but am unable to set root to (cd) or (cd0). I'm not sure these are the right devices. I also have made a Smart Boot Manager floppy which I have tried to boot using GRUB to no avail. I'm not sure what commands to do this either.

EDIT: Ok, I have gotten this to work. What I did was simply boot my Smart Boot Manager floppy using GRUB by using the root (fd0), chainloader +1, boot commands. This allows me to boot from CD although is a little robust considering I have to use a flash drive, a floppy, and the LiveCD.

---

