---
title: "Suspend2 works sortof"
date: 2007-05-28
forum: General Help
---

### Post by spotslayer on 2007-05-28
I have installed all of the suspend2 packages from Trevino's repository. This seem to mostly work however there a several things that I would like to sort out. I need help with this.

1)  Will suspend when lid closed, but only once. After first lid close I can still manually suspend.

2)  After any suspend and resume the processors are stuck at full speed. Can not even throttle them back              without log off.

3)   After a suspend and resume numlock is activated and I have to push Fn+NumLock twice to release.

4)   Originally when I pressed power switch would hibernate. Now pops up the normal shutdown screen. I am able to hibernate from there.

I am using a lenovo 3000 n100 that is all intel based. 2gb of ram. 4gb swapfile. Swap parameter is set in grub.

Would really like some help with the above.

I have one other question. I have set to S3. I understand that this write to hard drive and to ram and will restore from hard drive if battery is drained. Is my understanding correct?

David

---

### Post by firecat53 on 2007-05-29
I also have suspend2 installed, but via a patched and compiled kernel for AMD64. I also have the strange phenomena of the lid switch working once for suspend and then not again, though the suspend will still work vi fn-f5 and via menu. I've tried restarting hal, udev, acpi, and dbus, to no avail.

Unfortunately, I can't actually help or answer with any of your other issues, as I don't see the same results.

Good luck!

Scott

---

### Post by spotslayer on 2007-05-29
Thank's for the reply Scott.   I am still hoping for some help.

David

---

### Post by spotslayer on 2007-05-31
No help???

---

