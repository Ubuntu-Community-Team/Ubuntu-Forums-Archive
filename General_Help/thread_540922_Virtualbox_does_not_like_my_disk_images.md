---
title: "Virtualbox does not like my disk images?"
date: 2007-09-02
forum: General Help
---

### Post by Batuhan on 2007-09-02
Hello,

I had virtualbox running fine on my system(feisty) with WinXP(guest) on it. I recently reinstalled ubuntu(feisty again), and reinstalled Virtualbox on top of it. I create a new machine with Virtualbox, when it asks for the drive image I point it to the image I was using earlier and all goes fine.

But when I boot the machine it says "Disk read error, ctrl alt del to restart".

I have an image of a clean Winxp insallation image which I backed up earlier and it does not boot too.

Somehow, Virtualbox cannot see those images as bootable or something like that.

I think I'm missing something. What should I do to boot from my existing image files?

Thanks

---

### Post by kellemes on 2007-09-02
Not sure if I understand..
You have an image of an existing install? Or you have a copy of the install-cd?
As far as I know you can only fresh install Windows within the vm.

---

### Post by Batuhan on 2007-09-02
I have the disk image from an existing WinXp installation. The installation was done in Virtualbox.
It was the image file Virtualbox was using before.

---

### Post by Batuhan on 2007-09-03
Sorry for bumping, using existing images should be easy, what am I missing?

---

### Post by Batuhan on 2007-09-05
By installing the new vbox 1.5 I've solved the issue.

---

