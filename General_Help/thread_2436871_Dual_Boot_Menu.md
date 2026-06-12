---
title: "Dual Boot Menu"
date: 2020-02-14
forum: General Help
---

### Post by mraamohamed on 2020-02-14
Hello guys and thanks for the help in advance, OK here goes I am new to the world of Ubuntu and I have a question.  I have a dual boot system windows 10 and ubuntu 18.4 and I want to know when I reboot my system there is a menu that comes up to choose the OS i want to boot to can I change the order of the default sequence to Windows first vs Ubuntu first and how do I do this I have looked but can not seem to find a way to adjust that menu.

Thanks.

Abdulah

---

### Post by EuclideanCoffee on 2020-02-14
Yes, you will need to modify this order on your Ubuntu partition. Once you boot into Ubuntu, edit the following file.

Go to the dash and look for terminal. It is a block box with white font as an icon.

Write:

$ sudo nano [COLOR=#242729][FONT=Consolas]/etc/default/grub

Find "[/FONT][/COLOR]GRUB_DEFAULT=0"[COLOR=#242729][FONT=Consolas]

Change that to "[/FONT][/COLOR]GRUB_DEFAULT=saved"

You'll then need to update grub.

This is the command.

$ sudo update-grub

This will change the order of whatever you chose last. Helpful, huh?

If you want it set to Windows every time, you can likely get away with this command.

$ sudo grub-set-default 1

It makes the second option, likely your Windows computer, the first option. This isn't ideal because if this order changes, you'd have to change this number. It's hard to know before hand.

If you prefer a GUI, you can install the application that makes this easier.

sudo add-apt-repository ppa:danielrichter2007/grub-customizer
sudo apt-get update
sudo apt-get install grub-customizer

Type this in the terminal.

Then look for grub-customizer on the desktop.

---

### Post by mraamohamed on 2020-02-14
wow cool, thanks I will go try now thanks a lot for the help #ruze

---

