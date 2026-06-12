---
title: "How to make encrypted external drive to show up in the gui"
date: 2024-04-20
forum: General Help
---

### Post by Namal23 on 2024-04-20
I used this tutorial  [https://blog.stefandroid.com/2021/02/08/encrypt-usb-drive-with-luks.html](https://blog.stefandroid.com/2021/02/08/encrypt-usb-drive-with-luks.html) to encrypt my external drive with LUKS. It works all fine except it does not show up in the gui. So yeah, this is basically my question how to make it show up in the file manager after decrypting and mounting.

---

### Post by Holger_Gehrke on 2024-04-20
What version of Xubuntu are you using ? On Xubuntu 22.04 I can create an encrypted USB-stick (LUKS2) using the gnome-disks utility and if I plug it in I get asked for the password and then it comes up in Thunar as just another drive but showing an unlocked padlock on the icon.

Holger

---

### Post by Namal23 on 2024-04-20
I have 23.04. Thanks. If I unlock it with the gnome-disk-utility it actually shows up!!

---

