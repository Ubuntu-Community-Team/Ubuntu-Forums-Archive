---
title: "Arrow keys unresponsive in boot menu--cannot boot back into Windows10"
date: 2019-11-16
forum: General Help
---

### Post by jespody on 2019-11-16
Hey all. 
I am a noobish person when it comes to linux/ubuntu. I can do some basic stuff and am currently doing "The Odin Project" for web development.  In order to follow along the courses, I needed to have Ubuntu. Instead of using VirtualBox, I opted to dual-boot alongside Windows 10. Have had no problems whatsoever, other than a common wifi issue for my Surface Pro 3, but I fixed it. On to the problem!

Up until now, I havent tried to boot into windows because honestly...Boo to windows. 

*But i did try two days ago and my arrow keys will not work. They are completely unresponsive. Touch screen does not work in bootloader either (Im not sure if it is supposed to though) Basically I cannot find any way to boot back into windows. I have searched for a solution for few days and have not come up with anything yet. I have seen some issues people had which are kinda the same issue i have, though in those cases, they are using an USB keyboard. I am using Surface Pro 3, so its not an USB keyboard really...but it is technically an external keyboard i guess.

The only things I have done so far is:
apt-get upgrade
apt-get update
updated grub

Please, if anyone has any input, it'd be much appreciated. Thanks peoples :) 
Stay classy

edit: I am using Ubuntu 18.04

---

### Post by CatKiller on 2019-11-16
I don't know much about those machines, or their keyboards, but it seems unlikely that they'd bother to come up with a different protocol for the keyboard other than "USB with a different connector."

At the point that the Grub menu is active there is extremely limited support for hardware: no operating system has been loaded. Support has to come from the BIOS/UEFI, and they generally have an option exactly for handling USB devices without an OS, called "Legacy USB Support" or something similar. 

On UEFI devices you can reboot into the UEFI setup with ```
sudo systemctl reboot --firmware-setup
```

It may also be possible to use a similar command to boot into a different EFI entry, but that's not something I've ever tried to do.

---

### Post by jespody on 2019-11-16
Thank you so much. I will try as soon as I get back on my machine. Thanks for the reply :)

---

### Post by jespody on 2019-11-17
I tried this and no go. I got into the settings menu, but there was no legacy support. There was an option for an on-screen keyboard, but when i rebooted, that never showed. I have noticed a weird occurrence. I have been having general issues lately with the device. The device will get very hot, and then the device will get super slow n unresponsive to the point where I have to reset by holding the button down. When this happens, and ONLY when this happens. the keyboard works in bootloader and i can boot into windows. its bizarre. I have tried to just reset using the button without the device getting all Frackity and it doesnt work then either. I dont even know. If ya have any thoughts...let me know please. And thanks for your reply before again.,

---

### Post by CatKiller on 2019-11-17
For the topic of the thread, it's possible that you've got Fast Boot turned on in the BIOS, which skips a bunch of hardware detection things, and which is being bypassed by the hard reset. If it's not that, I'm out of ideas.

For the other thing, that's thermal throttling. *Something* needs to control your fans for them to work. That can be the BIOS/UEFI, or it can be software. If your Windows install was setup with software to control your fans, the ability for the BIOS to control it may have been disabled. The easiest approach is to re-enable it there. Otherwise the software that you'll need is **fancontrol** and **lm-sensors**, and you'll need the sensors included on the motherboard to be addressable. The ability to read particular sensor chips and write to fan controllers has to be reverse-engineered, so some chips work and some chips don't. Further discussion of that topic should go in a different thread, though: we want one problem and solution per thread so that people who might be able to help can do so, and so that later people with the same problem will be able to find solutions.

---

