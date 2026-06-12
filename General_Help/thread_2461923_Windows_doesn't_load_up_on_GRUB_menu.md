---
title: "Windows doesn't load up on GRUB menu"
date: 2021-05-10
forum: General Help
---

### Post by abhinavmir on 2021-05-10
I was trying to install Atomic Wallet, when my Ubuntu froze up for over 2 hours. I forced shut down from hardware, and now Windows doesn't load up in the grub menu. These are the things I've done.

```
sudo update-grub

```

From here, I tried to list the menulists from grub.

```
awk -F\' '/menuentry / {print $2}' /boot/grub/grub.cfg 

```

But I just saw Ubuntu.


```
Ubuntu
Ubuntu, with Linux 5.8.0-50-generic
Ubuntu, with Linux 5.8.0-50-generic (recovery mode)
Ubuntu, with Linux 5.8.0-48-generic
Ubuntu, with Linux 5.8.0-48-generic (recovery mode)
Ubuntu, with Linux 5.8.0-41-generic
Ubuntu, with Linux 5.8.0-41-generic (recovery mode)
UEFI Firmware Settings
```

---

### Post by yancek on 2021-05-10
Which release of windows are you using and is it an EFI machine?  Can you go into the BIOS firmware and select windows there?

You might try downloading and running boot repair from the site at the link below.  Use the 2nd option described on the page and when you run it, select the Create BootInfo Summary option and do not make any repairs.  Post the link you get when it finishes here.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

