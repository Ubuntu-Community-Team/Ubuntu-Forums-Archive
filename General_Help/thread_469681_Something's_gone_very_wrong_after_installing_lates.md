---
title: "Something's gone very wrong after installing latest updates"
date: 2007-06-10
forum: General Help
---

### Post by EvenStevens on 2007-06-10
The update manager popped up and installed the latest stuff and needed a reboot.
So I rebooted and when it came back, my network manager and beryl did not start  on boot.
It took them about 5 minutes to actually start up after Ubuntu started.

What the hell happened :|

Is there a way to Roll back to my original system settings before I updated?

---

### Post by EvenStevens on 2007-06-10
Obviously not?

---

### Post by steveneddy on 2007-06-10
choose the kernel before last from the GRUB menu.

---

### Post by Shazaam on 2007-06-10
Just as an experiment reboot your pc and choose an older kernel in Grub ie. choose 2.16.25 instead of 2.18.25 (example numbers) and see if everything works as before.

---

### Post by EvenStevens on 2007-06-10
Thanks for the advice.

Older Kernels didn't change a thing.

Is there like a system restore method in Ubuntu like in Windows or anything?

---

### Post by radioouman on 2007-06-10
I am having exactly the same problem.  My Grub boat loader doesn't show the Windows loader anymore, and I lost Beryl.  Nice updates....

---

### Post by LollYouSuckZor on 2007-06-10
Hint one, When you run Sudo apt-get upgrade, dont do that. :P

It never works.. manually install the updates by the way.  The only way to fix your problem is to do a clean install from a CD at this point.

---

### Post by mdurham on 2007-06-10
> **LollYouSuckZor said:**
> Hint one, When you run Sudo apt-get upgrade, dont do that. :P

It never works...

It's always worked for me!

---

### Post by EvenStevens on 2007-06-11
Okay, so I clean installed Ubuntu...then update manager popped up again on first boot and told me to update.

So I did.

AND IT HAPPENED AGAIN.

What file could be causing it? O_o

---

