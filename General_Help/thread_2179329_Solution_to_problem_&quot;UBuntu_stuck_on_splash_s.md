---
title: "Solution to problem &quot;UBuntu stuck on splash screen"
date: 2013-10-07
forum: General Help
---

### Post by pavacic-p on 2013-10-07
First go into the Advanced options in GRUB menu. [COLOR=#daa520]If GRUB menu doesn't show automatically hold down "Shift" key on boot up.
[/COLOR][IMG]http://img845.imageshack.us/img845/4033/io2i.jpg[/IMG]

In "Advanced options" select latest kernel that ends with "recovery mode".

[IMG]http://img593.imageshack.us/img593/4158/hven.jpg[/IMG]

In recovery mode options select root. [COLOR=#800080]Black box should open on the bottom of the screen[/COLOR].
Write [COLOR=#0000cd]sudo init 1[/COLOR]

[IMG]http://img823.imageshack.us/img823/49/bonf.jpg[/IMG]

After few seconds of you should see something like root@[name_of_PC] login:
Enter your username and hit enter.
Then enter your password and hit enter.

[IMG]http://img94.imageshack.us/img94/1112/jhv8.jpg[/IMG]

Welcome message should appear.
Enter [COLOR=#0000cd]jockey-text --list[/COLOR]
List of available drivers should appear.
Then write [COLOR=#0000cd]sudo[/COLOR] [COLOR=#0000cd]jockey-text --enable=[/COLOR][name_of_the_driver_from_the_list] - instead of [name_of_the_driver_from_the_list] enter name of your driver which starts from start of the line to the " - [description of the driver]"

[IMG]http://img545.imageshack.us/img545/4332/3amt.jpg[/IMG]

Then simply write [COLOR=#0000cd]sudo init 2[/COLOR]
It should automatically start GUI.
If it doesn't try writing [COLOR=#0000cd]sudo init 1[/COLOR]
If both fail try [COLOR=#0000cd]sudo reboot


[/COLOR]P.S sorry if it bothers you that my computer is on Croatian.

---

