---
title: "Ubuntu 20.04.3 Spontaneously Shuts Off"
date: 2021-11-06
forum: General Help
---

### Post by heinrichklopper on 2021-11-06
At random intervals, my laptop running Ubuntu will suddenly power off. There is no menu screen nor message of any sort before it powers off, as if I had unplugged a desktop. This did not happen on Windows (I'm dual-booting). Adding "nomodeset" to my "/etc/default/grub" fixes the problem, but prevents me from changing my screen brightness. Using Wayland as apposed to X11 does not help the issue. 
Computer specs:
Lenovo IdeaPad
Intel® Core™ i7-8565U
Mesa Intel® UHD Graphics 620

I would gladly share any necessary information. I have a file containing my /var/log/syslog specifically where I find a break in the timestamps while I was using it (indicating a power off). I have not yet attached it as I am unsure whether there is sensitive data contained within it.

---

### Post by ajgreeny on 2021-11-06
This could be caused by many different hardware problems from simply system overheating (fluff and dust build-up in the laptop?) to a bad RAM module or modules, or a bad power-supply unit.

---

### Post by dragonfly41 on 2021-11-06
My suggestion is that you need to try different modes of working to pin this down further. Trial and error.

You do offer the clue that  there are no such issues on Windows.
Have you tried creating a new user account in Ubuntu? Does the laptop power down in a new account?
Any problems if you leave LiveUSB running in "Try Ubuntu" mode?
Can you leave your laptop running in battery only mode?

---

