---
title: "EFI Dual Boot multiple options"
date: 2017-12-14
forum: General Help
---

### Post by thanekrios on 2017-12-14
Hello guys!

I'm facing a pseudo-problem, only because I'm crazy and want things in order. Here is the problem:


[IMG]https://i.imgur.com/GE7epMt.jpg[/IMG]


[LIST]
[*]I have entries of OSs that I no longer use (Antergos)
[*]I ahve 2 Ubuntu entries
[/LIST]

So I'm looking for a way to clean it up. Is there one?

Thank you!

---

### Post by yancek on 2017-12-14
You seem to be using UEFI so when booted into Ubuntu, open a terminal and run the command:  sudo efibootmgr   This will output the entries which are numbered and you can then delete what you want with the eifbootmgr command.  An example below if you have a boot entry numbered 0002, use the command below.  Just change the 0002 to what the entry you want to delete is.

> efibootmgr -b 0002 -B

---

### Post by oldfred on 2017-12-14
Some details on efibootmgr:

man efibootmgr

To see entries in order and details:
sudo efibootmgr -v

---

