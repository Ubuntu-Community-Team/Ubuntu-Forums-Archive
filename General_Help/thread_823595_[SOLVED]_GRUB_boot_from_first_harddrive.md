---
title: "[SOLVED] GRUB: boot from first harddrive?"
date: 2008-06-09
forum: General Help
---

### Post by justleen on 2008-06-09
Howdy folks!

I have a bootable USB stick with GRUB on it. i can add images/kernels to my stick and to GRUB without problems. But.. if I now leave my stick in, it will bot the grub there.. I would like an option "boot from first hard drive" (like the Live CD has). But i cant figure out what grub option i should use...

Any one here has an idea?

Cheers.

---

### Post by underdog512 on 2008-06-09
Thats really somthing that you set up in BIOS. Depending on your computer manufacturer you have to push one of the f keys upon booting to get into your BIOS setup utility.

Once in there you can edit you boot order. Just put the hard drive ahead of the usb drive in the boot order.

---

### Post by justleen on 2008-06-09
> **underdog512 said:**
> Thats really somthing that you set up in BIOS. Depending on your computer manufacturer you have to push one of the f keys upon booting to get into your BIOS setup utility.

Once in there you can edit you boot order. Just put the hard drive ahead of the usb drive in the boot order.

Cheers, but thats not what im after.. I want a grub menu option.. (not all BIOS have that interactive option.. like my laptop.. and my BIOS is pwd protected so re booting without the usb stick is much quicker..)

---

### Post by TeoBigusGeekus on 2008-06-09
What are the operating systems on your laptop?

---

### Post by justleen on 2008-06-09
> **TeoBigusGeekus said:**
> What are the operating systems on your laptop?

ubuntu only.

But.. i dont want to "hard-code" the root device. I just want a generic option to boot the first hard drive.

This is my "rescue stick". I have DSL, a Debian installer , and some tools on it. So if i plugged it into any system, i'd like to be able to boot the frist hard drive no matter what OS or system...

---

### Post by housam on 2008-06-09
I think that you should use an isolinux boot loader to setup something like that , I mean many boot options / destros to boot.

look at [[COLOR="Red"]_this thraed_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=703905") ( reply 7 ).

---

### Post by meierfra. on 2008-06-09
title Boot From First Hard Drive
chainloader (hd0)+1


title Boot From Second Hard Drive
chainloader (hd1)+1

---

### Post by justleen on 2008-06-10
Cheers Meierfra, thats what i was after..

---

