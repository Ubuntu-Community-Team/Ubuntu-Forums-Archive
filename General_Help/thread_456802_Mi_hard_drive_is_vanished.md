---
title: "Mi hard drive is vanished"
date: 2007-05-28
forum: General Help
---

### Post by endless_dark on 2007-05-28
Well, I'm very worried about this.

Today in the morning, I turned on my pc screen everything was normal. So, I tried to run a terminal, but it didn't started. It was weird so I tried to save the documents that were opened but it said the hard drive could not be written. So, a little scared I tried to reboot my computer.

But, when the pc is booting I recieve a message, something like: insert a bootable floppy disk. This is not a bootable disk.

Now I'm really scared. I booted with the ubuntu livecd inside and, ubuntu starts but I can't mount my hard drive, and when I run gparted it says that the 200GB of my hard drive are u nallocated.


Everything just blew away?? I know that I must burn important data in a dvd but I didn't and no,w I have lost everything?

---

### Post by The Noble on 2007-05-28
Weird, maybe your mbr got messed up. Try installing the grub again, maybe you will be lucky. As another hint, open up the inside of your computer and make sure the hd is seated properly; it may be jarred loose. If this fails, you may have had your hd crash. Download (or find) the cd your hd manufacturer supplies you with that does diagnostic runs on the hard drive. IT may be able to repair any bad sectors.

---

### Post by smoker on 2007-05-28
have you tried a disk check with fsck?

boot to the Ubuntu live cd and run
 > fsck -t ext3 /dev/hda1

if hda1 is your boot partition and the file system is ext3

---

