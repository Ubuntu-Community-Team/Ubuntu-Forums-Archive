---
title: "Weird Issue With Ubuntu Regarding Hot Keys"
date: 2020-02-24
forum: General Help
---

### Post by nakedgirl2 on 2020-02-24
On this computer, it has always had an issue with hot keys not  working, but the other computers don't. It has pretty close the same  specs, Intel 1151 processor, ASUS motherboards.
 The weird thing, my temporary fix is reset after a every reboot.

 I go to CCSM, and click enable 'Commands'. It works until I reboot.
 On the next boot, I have to un-click enable 'Commands' in CCSM for it to work.
 On the next boot, un-click enable.
 Next boot, click enable.
 That's what I don't understand.

Someone suggested I try installing Ubuntu on another computer that doesn't have this problem and then using that drive in this computer. Unfortunately, it didn't work.
EDIT: The hot keys work in Windows, so it's not a faulty motherboard, but a conflict with Ubuntu and the board software (UEFI). How do I fix it?
UPDATE: It is only in Unity, and it has nothing to do with the 'Commands'. When I enable or disables something in CCSM, it enables the hot keys until I reboot.


Computer Specs:
OS: Ubuntu 1804 (x64)
Motherboard: ASUS PRIME B250M-A
Processor: Intel® Core™ i5-6600K CPU @ 3.50GHz × 4
Storage Drive: Samsung SSD 850 EVO M.2 250GB
RAM: 16GB DDR4 2133 (x1)
Graphics: GeForce GTX 780 Ti

---

### Post by nakedgirl2 on 2020-02-24
Solved: I installed this PPA: sudo add-apt-repository ppa:unity7maintainers/unity7-desktop
It fixed it.

---

