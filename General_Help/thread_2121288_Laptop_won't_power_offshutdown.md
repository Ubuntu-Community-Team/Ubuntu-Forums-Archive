---
title: "Laptop won't power off/shutdown"
date: 2013-03-01
forum: General Help
---

### Post by Mists on 2013-03-01
I have an Acer Aspire 5560G-7809 that I am running Ubuntu 12.04 on. Through searching I have learned people with nvidia cards have been having this trouble, however I have an amd and have the "ATI/AMD proprietary FGLRX graphics driver (**experimental** beta) driver active. Changing video drivers did not fix this problem.


I have done this method:

```

1. Type in terminal: gksudo gedit /etc/default/grub
2. Find the line: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
3. Change this to: GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
4. Save the file and close the file.
5. Finally, in terminal: sudo update-grub
```

And it worked, but only once.. 

The screen goes to the Ubuntu screen with dots lighting up and gets stuck on one of them, this is what hitting ESC at the time told me:

```

unmount: /run/lock/: not mounted
unmount: /run/shm/: not mounted
Will now halt.
```


Anyone have any ideas?


(When I had Ubuntu 32-bit installed via WUBI it turned off fine. Now I am running Ubuntu 64-bit 100% on my disk, I have this problem.)

---

### Post by ptn107 on 2013-03-01
I am curious.  Try
```
sudo shutdown -P now
```
from a terminal on the desktop.  What happens?

---

### Post by gifford on 2013-03-01
Same problem here, but was able to work it out by using sudo update-grub and then sudo update-grub2.

---

### Post by Mists on 2013-03-01
> **ptn107 said:**
> I am curious.  Try
```
sudo shutdown -P now
```
from a terminal on the desktop.  What happens?

> **gifford said:**
> Same problem here, but was able to work it out by using sudo update-grub and then sudo update-grub2.



Tried what both of you said, same errors. 

:( Any other clues?

---

### Post by Mists on 2013-03-06
Still having this problem. :(

Anyone have more suggestions?

Thanks!

---

