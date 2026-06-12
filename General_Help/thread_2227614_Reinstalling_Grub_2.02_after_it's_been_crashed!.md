---
title: "Reinstalling Grub 2.02 after it's been crashed!"
date: 2014-06-03
forum: General Help
---

### Post by beyond32 on 2014-06-03
Hi. Any seggestions to how to reinstall grub 2.02 from a live usb on the hard drive? I've read methods for installing grub 2 (1.99) but they don't work for grub 2.02 that comes from trusty tahr.please help me, I cannot boot!
I've used this methods:[http://www.lancelhoff.com/restore-grub2-after-installing-windows/](http://www.lancelhoff.com/restore-grub2-after-installing-windows/)
but when i run "[FONT=Courier New]grub-install --recheck /dev/sda", it says in only one line that installatin is compelete and no errors reported, nothing more. And there is no difference after and before installing grub from this method![/FONT]

---

### Post by oldfred on 2014-06-03
May be best to see details. This may fix it as it will reinstall grub.

 
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by beyond32 on 2014-06-05
I've used boot-repair's recommended settings but things didn't change. This is the results before using boot-repair:[http://paste.ubuntu.com/7587166/](http://paste.ubuntu.com/7587166/) 
and this is the results after using it: [http://paste.ubuntu.com/7587183/](http://paste.ubuntu.com/7587183/)
And this may be important: "after I installed ubuntu 14.04 tusty tahr, the grub menu worked well until I replaced "grub", "grub.cfg" files and "grub.d" folder with the old ones from the ubuntu 12.02 Precise Pangoline installation! But fortunately I did a backup of new ones (by adding a _ to the beginning of their name." 
Now can I chroot the system folder, delete the old files and folder and then rename the new ones to their actual name?? But I don't khow how to do these!
Thanks in advance a lot for helping me!

---

### Post by oldfred on 2014-06-05
The 14.04 has a major update to grub2. You could change the settings or copy your 40_custom over, but should not attempt to change anything else.
Boot-Repair has a chroot and total purge & reinstall of grub. I would use that as it walks you thru the chroot.

Also looks like you have Intel & nVidia. See links in my signature (most is UEFI, but dual video links would be the same) although with the very newest nVidia, bumblebee may not be required.

---

