---
title: "Meh im done with linux ...but i need help."
date: 2008-04-13
forum: General Help
---

### Post by 500sd on 2008-04-13
Ok well when i installed linux i gave it 30 gb of my hdd, but now i want to remove linux and give that 30gb back to my windows partition. How would i do this?

---

### Post by Saint Angeles on 2008-04-13
boot up a live CD and open up gparted... from there you can do all kinds of stuff to your partitions.

(you can't do that with windows... thats just one example)

---

### Post by 500sd on 2008-04-13
Hmm ok thanks lol I guess it's more simple than i thought it would be

---

### Post by p_quarles on 2008-04-13
> **500sd said:**
> Hmm ok thanks lol I guess it's more simple than i thought it would be
That's more simple than it actually is, in fact. You will also need to restore the Windows MBR. If you leave GRUB configured as is, it will refuse to boot after you remove the Ubuntu partition.

---

### Post by sayakb on 2008-04-13
> **p_quarles said:**
> That's more simple than it actually is, in fact. You will also need to restore the Windows MBR. If you leave GRUB configured as is, it will refuse to boot after you remove the Ubuntu partition.

 Just as p_quarles said, you have to restore the MBR. Boot in to your Windows setup CD/DVD, at the first screen, select recovery mode to enter console. There, type: ```
fixboot
fixmbr
``` 
Grub would be lost and you would boot in straight to Windows.

---

### Post by alexsabree on 2008-04-13
You could also boot to your windows disk and use the repair option.

---

### Post by 500sd on 2008-04-13
Uh wait im soo confused now lol
what do i have to do? 
i dont have my windows disk ...is that a problem?

---

### Post by p_quarles on 2008-04-13
> **500sd said:**
> Uh wait im soo confused now lol
what do i have to do? 
i dont have my windows disk ...is that a problem?
Yes, because not having recovery media is asking for a disaster. 

It doesn't prevent you from fixing the MBR though. Look here:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

### Post by 500sd on 2008-04-13
o.O that page is MASSIVE ...what do I need to follow there?

---

### Post by Saint Angeles on 2008-04-13
i have something called "super grub disc" that can fix windows boot also... i'm not sure about the URL (just google it)

hope that helps!

PS if you are gonna use windows, you'd better get real familiar with how to reformat drives and such. you'll need to do it about every 6 months to keep your computer running smoothly. JK (kind of)

---

### Post by 500sd on 2008-04-13
what do you mean it can fix windows boot?

---

### Post by bingoUV on 2008-04-13
If 500sd  has a separate /boot partition, he will not need to do anything to MBR right? I partition my disk manually, so I have forgotten whether ubuntu creates a /boot partition by default. Does it?

---

### Post by p_quarles on 2008-04-13
> **500sd said:**
> what do you mean it can fix windows boot?
When you installed Ubuntu, the program which boots up the operating system was replaced. The one Windows uses is not capable of booting multiple OSes, so this is necessary. 

In order to go back to a single-boot system, however, you will need to reinstall the Windows bootloader into your MBR (master boot record). The Super GRUB disk contains an option (under the "windows" menu) to do this.

---

### Post by 500sd on 2008-04-13
Ok so is this what i need?

[http://www.supergrubdisk.org/forum/index.php?topic=44.0](http://www.supergrubdisk.org/forum/index.php?topic=44.0)



EDIT: I'm gonna go sleep now...dont abandon this thread though ;) 
So basically the super grub can remove my linux partition, give the space back to my windows partition, and re-install my MBR?

---

### Post by p_quarles on 2008-04-13
No, use the link I gave you earlier. The one in your post appears to be a modification that's designed to automatically restore the Linux bootloader, which is the opposite of what you want. ;)

The regular disk (the link I gave you) isn't that hard to use. You'll need to burn it like you did the Ubuntu disk, boot from it, and follow the steps to restore the Windows bootloader. 

The Super GRUB disk won't erase your Ubuntu partition, though. As the second post in this thread mentioned, you'll need to use the live disk to do that. Alternatively, you can use the Gparted live disk, which imho is more intuitive and easier to do than using the Ubuntu disk for partitioning. 

In any case, it all sounds more complex than it actually is. Don't hesitate to ask further questions, but do please be as specific as possible about what part(s) you're unsure about.

---

### Post by 500sd on 2008-04-13
Ok thanks
What should I do first though? Remove the partition or restore the MBR?

---

### Post by p_quarles on 2008-04-13
If everything goes correctly, the order won't matter. If I were you, I'd restore the MBR first, as that is the part that's crucial for being able to boot the system.

---

