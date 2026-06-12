---
title: "Problems With Grub"
date: 2006-07-25
forum: General Help
---

### Post by Musicalmidget on 2006-07-25
Hello.

I think this is more a problem with Grub than with GNOME, so I hope this is the correct place to ask for help. 

I used to have my PC setup to Dual Boot XP Home and Ubuntu 5.10.  Unfortunately however, I recently had to reinstall XP and subsequently the MBR was overwritten and I could no longer boot Ubuntu once XP had been reinstalled.

Today, I restored GRUB by inserting my Ubuntu Disk and typing "rescue" at the "boot:" prompt.  When prompted to do so, I selected the partition which Ubuntu was installed to and typed "grub-install /dev/hda1" to reinstall grub.

Now, I can choose at startup again which operating system  to boot, although I'm now having problems of a different nature.  The list shows Ubuntu and XP Home just like it used to, and selecting Ubuntu boots it as expected.  Selecting XP to boot however simply reloads the selection screen and I can't get past it.

I have so far been unable to fix this problem, so any advice would be very much appreciated.

Thanks.

---

### Post by pablojc on 2006-07-25
hi, well i see that you made a mistake(i also made it).
you had to put

**grub-install /dev/hda**(without "1")

instead of 

**grub-install /dev/hda1**

the thing is that i don't know how to fix this, because just today i get this problem, i hope someone could help us.

---

### Post by pablojc on 2006-07-25
i have found this from another forum:

```
http://www.linuxquestions.org/questions/showthread.php?t=242025
```

---

### Post by Musicalmidget on 2006-07-25
Hi again.

Shortly after posting I found the same question that is linked to in the post above.  Unfortunately though, the FIXMBR command didn't seem to fix my MBR at all.  Instead, it seems to have broken it.  After doing so, I wasn't able to boot to Ubuntu *or* Windows.

I've ended up doing a full system reinstallation and have only just managed to get online and running again.

Thank you for the help though, I do appreciate it. :)

---

