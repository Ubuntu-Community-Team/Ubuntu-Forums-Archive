---
title: "How to skip the cryptsetup password at boot time ?"
date: 2012-11-24
forum: General Help
---

### Post by gyyug78fg87ogguiioioioioi on 2012-11-24
[SIZE=2]In Lubuntu 1[SIZE=2]2[/SIZE].10, at boot time, cryptsetup asks me for the password of a partition.[/SIZE]

[SIZE=2]I don't want to have to enter the password at each boot since I don't need
to use the encrypted partition.[/SIZE] 

[SIZE=2] How do I stop cryptsetup from asking me for the password at every boot ?[/SIZE]

---

### Post by gyyug78fg87ogguiioioioioi on 2012-11-24
anybody

---

### Post by slabo on 2012-11-25
You could try this: Comment out the line in /etc/crypttab that refers to your partition. Also comment out the respective /dev/mapper-device in /etc/fstab, if there is one.

---

### Post by gyyug78fg87ogguiioioioioi on 2012-11-25
how do i "Comment out"?
sorry i dont understand the way you explain:confused:

---

### Post by slabo on 2012-11-25
Open the file /etc/crypttab with an editor, for instance with nano like:

```
sudo nano /etc/crpyttab
```

Then, identify the line that refers to the partition in question. Put "#" (withouth quotation marks) at the beginning of the line. Also, remember the name of the device that cryptsetup supplies for this partition, that should be the word that was at the beginning of the line.

Save the file, close it and open /etc/fstab

```
sudo nano /etc/fstab
```

Find the line that contains "/dev/mapper/<devicename-from-crypttab-above>", if there is one. Put a # at the beginning of that line, save, exit, reboot.

If anything is unclear, please ask again.

By the way, you should also be sure that you don't disable this for the system partition. You said you don't need the encrypted partition so i assume your system partition is not encrypted. If you chose full disk encryption at installation, be sure that you disable the right partition only. If you should disable unlocking of the system partition, it will be possible but a hassle accessing your system, and you will probably need a bootable usb-stick. If you are unsure, we should try to figure out first exactly which partition is which.

---

