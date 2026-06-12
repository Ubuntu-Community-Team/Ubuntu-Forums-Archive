---
title: "booting 3 operating systems"
date: 2013-09-12
forum: General Help
---

### Post by darryl2 on 2013-09-12
I have  linux with a wubi install of ubuntu on my xp computer. I have been trailing mint 13 on a flash drive and have liked what i see but its really slow booting. So I would like to install it on my computer dual booted with my xp os. My question is will I still have the option to boot to ubuntu as well as mint and xp if I do the full install.
thanks

---

### Post by mastablasta on 2013-09-12
wubi installs Ubuntu inside a virtual drive inside windows. so you sould be able to boot all 3 but you will have only 2 in grub. if you plan to install side by side.
if oyu like mint then just install that one into empty (unformated) disk space. remove ubuntu and use mint. i mean it's not like you will be using all 3 operating systems. and if you need to it is better to invest into ram and CPU and use virtualbox.

---

### Post by Mephisto Pheles on 2013-09-12
I have a similar setup, Linux Mint installed on HD, xubuntu on wubi and Win XP.
If you install Mint you will get a boot menu (Grub), there you can choose to boot either Mint or XP.
If you choose XP you'll go into the boot.ini Win menu, the one you boot into now,
there you can choose Win or your Ubuntu wubi install.
 wubi is always linked to windows, therefore it is in the Win boot menu and not the initial Grub menu.

You can install as many different distros as you have room for on your HD.
Not that it would make much sense unless you really enjoy experimenting.
The wubi ubuntu doesn't even count, because it is basically a large windows file.
It's actually a Windows program.

I just migrated my wubi xubuntu, as a backup, on its own partition.

I have seen many people comment wubi is slower than a regular install,
I still have to experience that to be honest.
In normal use I don't notice any difference. 
If anything my xubuntu wubi feels snappier than Mint most of the time.
Probably because Mint gets used much more and has more programs installed.

Maybe for really disk intensive things it makes a difference.
Running a webserver and a large website running on a mysql server with a large database on wubi is probably not a good idea ;)
- mephisto

---

