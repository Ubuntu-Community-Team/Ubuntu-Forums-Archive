---
title: "GRUB help"
date: 2008-04-12
forum: General Help
---

### Post by sixstorm on 2008-04-12
Hey guys.  I tried to install the 8.04 beta but apparently my CD is bad.  That didn't stop it from deleting the partition with GRUB on it, thus GRUB giving me error 15.  I tried to load up the LiveCD and go through the GRUB CLI but I'm getting error 17 when trying "find /boot/grub/stage1".  Ive got a Vista partition on there and I'd like to at least get to it for the moment.  I'm not around any blank CD-Rs or my Vista disc, so I'd like to know what I could try with the 8.04 beta Live CD.  Any hints?

---

### Post by tamoneya on 2008-04-12
give [super grub]("http://supergrub.forjamari.linex.org/") a try.  It should simplify the installation.

---

### Post by sixstorm on 2008-04-12
> **tamoneya said:**
> give [super grub]("http://supergrub.forjamari.linex.org/") a try.  It should simplify the installation.

I don't have any CD-Rs right now.  I can wait until tomorrow morning to get my Vista disc and recover the Vista bootloader.  BUT, I want to see if there was anything I could do with my LiveCD.

---

### Post by sixstorm on 2008-04-12
I really wish Ubuntu would just seamlessly blend in with the XP or Vista bootloader . . .

---

### Post by sixstorm on 2008-04-13
Well, I re-loaded the Vista bootloader with the Vista install DVD, then noticed that the ISO I downloaded was corrupt.  Now I am posting from Ubuntu 8.04 beta this morning and wow . . . what an upgrade!  Almost everything worked!  Thanks for your help guys.

---

### Post by hurtstotalktoyou on 2008-04-13
> **sixstorm said:**
> Hey guys.  I tried to install the 8.04 beta but apparently my CD is bad.  That didn't stop it from deleting the partition with GRUB on it, thus GRUB giving me error 15.  I tried to load up the LiveCD and go through the GRUB CLI but I'm getting error 17 when trying "find /boot/grub/stage1".  Ive got a Vista partition on there and I'd like to at least get to it for the moment.  I'm not around any blank CD-Rs or my Vista disc, so I'd like to know what I could try with the 8.04 beta Live CD.  Any hints?

Technically speaking, you don't *need* to do the stage1 command.  I recommend assuming your root is (hd0,1) and skipping that step.

1.  Open terminal (applications > accessories > terminal)
2.  Type "sudo grub"  - the grub prompt should then appear
3.  type "root (hd0,1)"
4.  type "setup (hd0)"
5.  type "quit"
6.  reboot

Hopefully that should do it.  However, if it doesn't, you can try typing "sudo gedit /boot/grub/menu.lst" in terminal and figuring out your root drive that way.

Good luck!

---

### Post by hurtstotalktoyou on 2008-04-13
> **sixstorm said:**
> I really wish Ubuntu would just seamlessly blend in with the XP or Vista bootloader . . .

As annoying as grub can be, the windows bootloader is even worse.

---

