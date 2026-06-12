---
title: "Problem with grub"
date: 2024-06-02
forum: General Help
---

### Post by mussassa on 2024-06-02
I did a dual boot installation of Ubuntu 24.04 and Windows 10 but every time I boot Windows 10 and restart the grub disappears. I usually have to change the boot order on the BIOS to restore the grub. I am looking for a permanent solution to this problem.

---

### Post by yancek on 2024-06-02
You should be able to change the boot order permanently from the UEFI BIOS on your computer.  How this is done depends uponw/ the computer manufacturer so you will need to go into the BIOS and look for that option or do an online search for it with the specific type computer you are using which we don't kno

---

### Post by currentshaft on 2024-06-02
The problem is Windows, the upstanding OS citizen it is, has its NTLDR overwriting GRUB.

You should be able to "fix" it by modifying the Windows registry or using a tool like EasyBCD. I don't use Windows and have no first-hand experience with either, so try those at your own risk.

---

### Post by oldfred on 2024-06-02
Both Windows updates & major grub updates, will reset boot order to have that system as first.
Is Windows doing a lot of updates?

What brand/model system?

Unless an HP and a very few others, you can use efibootmgr in Ubuntu to reset boot order.
man efibootmgr

to see entries & current order by number
sudo efibootmgr -v
and then -o parameter with numbers in order you want.

---

### Post by dragonfly41 on 2024-06-02
There is EasyUEFI which runs in Windows.

---

### Post by mussassa on 2024-06-03
> **currentshaft said:**
> The problem is Windows, the upstanding OS citizen it is, has its NTLDR overwriting GRUB.

You should be able to "fix" it by modifying the Windows registry or using a tool like EasyBCD. I don't use Windows and have no first-hand experience with either, so try those at your own risk.
Thank you

---

