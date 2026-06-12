---
title: "Attractive boot screen for dual booting?"
date: 2014-09-17
forum: General Help
---

### Post by Garnett on 2014-09-17
I've got a new Win8 laptop on the way and want to set it up for dual, or triple boot.

I would like to have a decent looking boot options screen but it looks like grub2 hasn't moved on much recently.

Please can anyone help point me in the direction of more things to read up on?

---

### Post by deadflowr on 2014-09-17
There's an entire thread on grub2 themes here
[http://ubuntuforums.org/showthread.php?t=1823915](http://ubuntuforums.org/showthread.php?t=1823915)

look over a few, see any peaks your interest.

---

### Post by oldfred on 2014-09-17
If you want to install another boot manager and have UEFI you can install rEFInd. It uses icons, see links for example.
UEFI and grub are boot managers in that they let you choose what to boot. And grub is also a boot loader or required to start Ubuntu.

       [http://www.rodsbooks.com/refind/index.html](http://www.rodsbooks.com/refind/index.html)
[http://www.rodsbooks.com/refind/secureboot.html](http://www.rodsbooks.com/refind/secureboot.html)
Now has a ppa to make it easy to install:
[http://www.rodsbooks.com/refind/getting.html](http://www.rodsbooks.com/refind/getting.html)

---

### Post by grahammechanical on 2014-09-17
Look in the software centre for grub2-splashimages. Those will install into /usr/share/images/grub/. Select one and copy and past it into /boot/grub/. And then run

```
sudo update-grub
```

and the next time you boot there will be the back ground image of your choice. You will need to run the File Manager with Administrator/Root privileges to paste the image file in /boot/grub/. How to do that is another subject. If you are familiar with gksudo then you know what to do except for the fact that gksu is not installed by default any more. The developers cannot understand why anyone would want to edit system files so they have depreciated gksu.

Regards.

---

### Post by Mark Phelps on 2014-09-17
GRUB2 is text-based, so while you can add a background, it still is just text.

There is BURG, which is graphical, but Ii haven't used it myself.

---

### Post by oldfred on 2014-09-17
Not sure if there is a newer burg somewhere but these sites all show it as old.

 Newer Burg  as of 
[https://aur.archlinux.org/packages/burg-efi-x86_64-bzr/](https://aur.archlinux.org/packages/burg-efi-x86_64-bzr/)
As of 2012-03-10 orphaned this package in Arch, switch over to grub2-efi-bzr . 
This burg shows last update Oct 2010
[https://code.google.com/p/burg/downloads/list](https://code.google.com/p/burg/downloads/list)

---

### Post by fantab on 2014-09-18
You can also consider using [EasyBCD]("http://neosmart.net/EasyBCD/") as an alternative Windows boot loader. EasyBCD can boot Linux as well and its 'free' for non-commercial use.

Burg is not in active development... do not use it.

---

