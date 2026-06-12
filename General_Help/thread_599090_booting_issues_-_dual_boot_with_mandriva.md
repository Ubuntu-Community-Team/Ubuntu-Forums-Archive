---
title: "booting issues - dual boot with mandriva"
date: 2007-10-31
forum: General Help
---

### Post by bluepowder7 on 2007-10-31
i have had ubuntu feisty fawn 7.04 set up and running on one of my partitions for a while now, and decided to add mandriva-one spring 2007 whatever onto another partition.  it went through the install, and it lets me edit the boot loader options.  the install consisted of formating a partition that was already set aside a while ago, and letting mandriva do its thing on the existing /boot, existing /home, existing swap, and new /root partitions.

when i try to boot into mandriva, it works perfectly fine, but when i select to boot into ubuntu i get a bunch of file system check errors, mounting errors,  and so on.  in the end, it stops the booting with a terminal prompt!  the last few lines that i can see (can't scroll up to see too far back) are "File system check failed", "A maintenance shell will now be started", and "The program 'apt-get' is currently not installed.  You can install it by typing:  apt-get install apt" - it says this last part twice.  i can type "exit" and it continues to boot into ubuntu (but quickly spits out a bunch of other worrisome messages), but it's weird - blue background, ethernet card not functioning (laptop), etc.

(as an aside, the boot options are showing on a mandriva background, which is weird cuz i would have thought it would be a basic black DOS-ish background with normal text.)  anyhoo, once i get into mandriva, here's the boot options that i can make (note that these are GUI fields):


MANDRIVA (boots fine):
Label:   Mandriva (this is a field i can edit to make life easy)
Image:  /boot/vmlinuz (i can pull down other options here, like vmlinuz-2.6.20-15-generic and so on)
Root:  /dev/sda6
Append:  resume=/dev/sda2 splash=silent (sda2 is my swap partition)
Video mode:  (i have this left blank - seems to boot fine into 1440x900)
Initrd:  /boot/initrd.img  (here i can also pull options like initrd.img-2.6.20-15-generic)
Network profile:  (blank again)


UBUTU (spits out errors and boots into a half-crippled OS):
Label:   Ubuntu (this is a field i can edit to make life easy)
Image:  /boot/vmlinuz (i can pull down other options here, like vmlinuz-2.6.20-15-generic and so on)
Root:  /dev/sda5
Append:  (blank - hmm, should it have the swap partition indicated like mandriva does???)
Video mode:  (blank)
Initrd:  /boot/initrd.img  (here i can also pull options like initrd.img-2.6.20-15-generic)
Network profile:  (blank again)


the kernel options i have are:

2.6.20-15-generic
2.6.20-16-generic
2.6.17-13mdvlegacy
none (as in no kernel info appended - see Image and Initrd lines above)


should i specify kernels in some of those lines?
does the "Append:" line need to have something there?

lastly, does having the bootloader show up with a fancy graphics background make ANY difference?  if i want something basic and old-school, how do i do that?

---

### Post by bluepowder7 on 2007-11-01
by the way, there's another screen in the bootloader setup GUI.  it says:

Boot device:  /dev/sda (ATA HTS54... blah blah blah)

should it be /dev/sda like it currently is?   or /dev/sda1 which is the actual /boot partition?

---

### Post by bluepowder7 on 2007-11-01
le bump?

---

### Post by bluepowder7 on 2007-11-01
alright, screw it.  :P  i'm reformating it all and reinstalling Ubuntu yet again (this is probably the 5th time i'm going through the process - getting better at setting up my wireless card at least!   haha!!)  somewhere i saw mention that any time i install a new OS, i shouldn't let it touch the MBR and should make it install its crap onto its own /root partition.  maybe that's what i did wrong when i installed mandriva...???

---

