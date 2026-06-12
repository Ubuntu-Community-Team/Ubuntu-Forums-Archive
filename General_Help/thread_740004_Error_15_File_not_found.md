---
title: "Error 15: File not found"
date: 2008-03-30
forum: General Help
---

### Post by RedStar1916 on 2008-03-30
I don't know how it happened, I haven't installed any new OS or been playing around with any important files, but all of a sudden whenever I try to boot I get an Error 15: File not found. I've done some research on this and apparently it means that one of the GRUB files is missing, so I tried to reinstall GRUB as per [this]("http://ubuntuforums.org/showthread.php?t=224351") thread.
Running the "find" command returned "(hd0,0). Other than that the only noteworthy output I got during the install was when I ran "setup (hd0)", I got this:
```
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

```
That led me to believe that everything had gone off without a hitch, however when I restarted to laptop without the live CD I got the exact same problem.

Can anyone help?

---

### Post by RedStar1916 on 2008-03-30
bump...

---

### Post by oldos2er on 2008-03-30
Can you post the output of cat /boot/grub/menu.lst ?

---

