---
title: "Input devices not working after upgrade to kernel 3.13.0-24"
date: 2014-05-04
forum: General Help
---

### Post by aksel-r on 2014-05-04
Hi all,

I upgraded installed the latest kernel, v [COLOR=#000000]3.13.0-24. I had some serious boot-issues after that, had to create a new initramfs image using "update-initramfs" and re-create my GRUB2 menu, but that is really another story since I did get the system to boot.

Now I am stuck at my login screen, because no input devices work. I have a wired USB keyboard and a wireless bluetooth keyboard, none work.

I have tried plugging it in to different USB ports, USB3 and USB2. I have legacy USB support in BIOS enabled, and I have tried disabling it, as well as disabling only USB3 legacy support.

I have an Intel H77-based Asus motherboard. 

I am running Ubuntu x64 13.10.

I booted into a 14.04 LiveCD, mounted my file-system and outputted some logs for debug purposes:

[LIST]
[*]Output of dmesg - [http://paste.ubuntu.com/7392019/](http://paste.ubuntu.com/7392019/)
[*]/var/log/Xorg.0.log - [http://paste.ubuntu.com/7392022/](http://paste.ubuntu.com/7392022/)
[*]/var/log/syslog - [http://paste.ubuntu.com/7392024/](http://paste.ubuntu.com/7392024/)
[*]/var/log/boot.log - [http://paste.ubuntu.com/7392030/](http://paste.ubuntu.com/7392030/)
[/LIST]

I cannot seem to find any related errors in those logs. Searching for the string "[/COLOR][COLOR=#000000]Logitech Illuminated Keyboard[/COLOR][COLOR=#000000]" (my keyboard) in the dmesg output reveals that it seems to be detected just fine.

Anybody have a clue what might be going on, or how I can further debug this stuff?

Thank you![/COLOR]

---

### Post by aksel-r on 2014-05-06
Gentle bump..

No-one has a clue?

I'm really not sure if this is a USB-problem at all. The whole machine is acting weird. I cannot SSH into it for example, although it seems to be idling at the login screen (the cursor in the password field is blinking).

Also, I can reach the GRUB menu by holding shift down during bootup, but then when I choose to boot in recovery mode and the Recovery Menu appears, and my keys arent working. I can't select options in the Recovery Menu.

This is weird. The symptoms aren't really telling me much, and neither are the logs. 

My system is rendered useless. Any help is greatly appreciated!

---

