---
title: "Please help me how to reboot the system."
date: 2013-05-08
forum: General Help
---

### Post by kingofhearts26 on 2013-05-08
When I open my laptop after the Logo kata the "Reboot and Select proper boot device or insert boot media in selected boot device and press a key". And I don't know how to do it. Can anybody help me please. Any help is appreciated. thank you.

---

### Post by Bashing-om on 2013-05-08
kingofhearts26; Hi !
Please provide additional info in order to properly respond to you question.

Single booting some version/distro of 'buntu ?
Dual boot ? what ?
Have you recently reset any of the BIOS default parameters ?
Can you boot up a live/CD/DVD/USB/ ?

Please describe your boot process and what is happening in great detail -> what you expect to happen as opposed to what does transpire.
[INDENT=2]
kind regards

[/INDENT]

---

### Post by kingofhearts26 on 2013-05-08
The problem is that when I push the power on, there's something appear "Reboot and select proper boot device or Insert boot media in selected boot device and press a key" on my laptop. I don't know why, and i can't get to the main set up where you can see the recovery mode settings. It just keep on pop-in the "Reboot and Select proper boot device or Insert Boot media etc. please help.

---

### Post by grahammechanical on 2013-05-08
When we switch on the machine it loads a boot system that is either BIOS (Boot Input Output System) or EFI (Extensible Firmware Interface). This has instructions such the order in which to look for an operating system . If it does not find an operating system it will give an error message such as the one that you are seeing.

Do you have any operating systems on the hard disk? Have you tried putting a Ubuntu Live DVD into the DVD drive and then rebooting. If you have more than one hard disk it may be that you have set the boot system to look for an operating system on a hard disk that does not have an operating system on it. May be the hard disk is broken.

Regards.

---

### Post by kingofhearts26 on 2013-05-08
Yes, I already tried that one. And it didn't work. Also, I did not try to put a Ubuntu Live DVD into the DVD drive 'cause I'm using miniBook. So it doesn't have any DVD drive or any disk drive that can be used. That's why I'm having a hard time fixing my miniBook.

---

### Post by greatsirkain on 2013-05-08
Sounds to me like the boot sector of your hard drive is bust.
Try booting with a live version of Ubuntu from a USB stick. There're loads of programs to make one if you don't have one already (unetbootin if you're using linux or sardu if you're using windows). Both programs install everything you need (if using unetbootin make sure you select 'live' in the version when you've selected the OS)

---

