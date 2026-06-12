---
title: "/boot/memtest86+.elf Possible Unix/Heuristic-90 (not disinfectable)"
date: 2017-08-18
forum: General Help
---

### Post by davidrqgamer on 2017-08-18
I used F-Prot to scan for viruses and i got the message /boot/memtest86+.elf Possible Unix/Heuristic-90 (not disinfectable)

How do I remove the virus thank you

[ATTACH=CONFIG]276441[/ATTACH]

---

### Post by deadflowr on 2017-08-18
False positive, more likely.
That's a program, usually selected at boot, to run memory scanning tests.
Used to test your RAM for defects.

But it's easy to remove (and reinstall) if you want,
just open a terminal and run
```
sudo apt-get remove memtest86+
```
to remove

and
```
sudo apt-get install memtest86+
```
to reinstall again.

---

### Post by davidrqgamer on 2017-08-19
Thank you very much Bless you

---

