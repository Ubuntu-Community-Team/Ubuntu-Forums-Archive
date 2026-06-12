---
title: "Ubuntu 18.04 locking up screen/keyboard/mouse"
date: 2020-03-25
forum: General Help
---

### Post by nitsujz28 on 2020-03-25
Couldn't find the right answer elsewhere, and I not only want to fix it but I want to learn how to troubleshoot this stuff for the future.

I just did a fresh reinstall of Ubuntu 18.04.4 (Kernel release 5.3.0-42-generic) from a freshly burned DVD. Previously had 18.04 without these problems, but at that time I had no sound (dummy output) so I decided to reinstall, previous problems assumed to be unrelated. The only software I've installed so far is NordVPN.

Problem 1: Random freeze of the screen, keyboard, and mouse. If sound is playing it will continue, but no screen motion and no actions from keyboard or mouse. I have to hard reset machine.

Problem 2: Screen turns into a checkerboard mess but mouse and keyboard functions work. Sometimes it's a quick flash, sometimes it remains indefinitely and I must reset which I'm able to do with the mouse clicks.


Where does one begin? What other info will I need to provide to find help? System Monitor shows low RAM and CPU usage and it still occurs. I have not been able to find a pattern or replicate it intentionally. I appreciate all advice and help!

---

### Post by nitsujz28 on 2020-03-26
It will probably help to mention that all computer components are from 2013 and include:
- Motherboard = Gigabyte GA-990FXA-UD3 (rev. 4.0)
- CPU = AMD 6-CORE FX-6300 3.5G 8M R
- Graphics card = EVGA GeForce GTX 650 Ti BOOST
- RAM = G-Skill RIpjaws X 8gb
- Storage = Samsung 840 Evo SSD(120gb) and WD green hdd (2tb)


I've done a bit more searching for solutions, but nothing that has helped me yet..

---

### Post by lvm on 2020-03-26
I would've start tinkering with the graphics driver. With 18.04 ubuntu installs kosher open-source noveau driver for nvidia cards by default, but it's crap. It caused random lock-ups on one of my systems too. Try installing proprietary nvidia driver.

---

### Post by nitsujz28 on 2020-03-27
Thanks for your response. That makes sense and I will try that now.

Would it explain keyboard lock up? I've confirmed that locks up as well because when music keeps playing during the frozen screen, my keyboard's volume buttons no longer work.

---

### Post by lvm on 2020-03-27
In my case noveau started blocking CPU cores until everything locked up - keyboard, mouse, network. But yes, I do recall that sound continued playing for some time after the computer stopped reacting to keyboard including combinations that should always work like ctrl-alt-Fn

---

### Post by nitsujz28 on 2020-03-31
For future reference, my problem seems to be solved by lvm's advice. I switched to the proprietary driver "metapackage from nvidia-driver-435 (proprietary, tested)", rather than the open source one that it was by default.

---

