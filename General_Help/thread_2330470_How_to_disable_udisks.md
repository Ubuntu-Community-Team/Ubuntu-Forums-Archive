---
title: "How to disable udisks ?"
date: 2016-07-11
forum: General Help
---

### Post by grox2 on 2016-07-11
Hello everyone, I've been using Linux for a little time now, and I recently acquired a ChromeOS. I installed crouton to extend it with a full Ubuntu distro, and felt upon a problem.
When I insert my SD card, the Unity desktop environment mounts it and everything's ok. But then, udisks comes and try to mount it a second time ; asking for my password. I personnally find it extremely annoying as udisks ask for my password each time I close and open my laptop's lid, which is very counter-productive. Plus, it's useless as the SD card is mounted by Ubuntu and I don't use udisks.
I tried to uninstall it but Nautilus automatically uninstalled too (dependencie problem) and without it, I can't have a background image for instance.
So, I was wondering if I could disable udisks or just tell him to ignore everything.

Thanks in advance !

---

### Post by DuckHook on 2016-07-12
To my knowledge, udisks is an integral part of your OS and must not be uninstalled. Doing so will break your system. Its job is to detect new mountable media and mount them. You cannot disable it without major system surgery, nor should you. However, there is a way to make it ignore any one sdcard, though it will then ignore all cards of that manufacturer and type. Note: instructions are convoluted and quite involved, but it can be done: [http://askubuntu.com/questions/301122/prevent-a-specific-usb-device-from-auto-mounting](http://askubuntu.com/questions/301122/prevent-a-specific-usb-device-from-auto-mounting)

---

