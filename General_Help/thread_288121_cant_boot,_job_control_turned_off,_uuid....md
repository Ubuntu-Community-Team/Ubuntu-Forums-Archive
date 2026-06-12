---
title: "cant boot, job control turned off, uuid..."
date: 2006-10-29
forum: General Help
---

### Post by crash0 on 2006-10-29
hello.

i have a big problem in edgy right now. when i try to boot, the following message appears
> cant acces tty job control truned off

right now i am typing from the live cd, the keyboard is all messed up and it took me about 10 minutes to write this. i googled around and learned that this happens when grub or something gets the UUIDs mixed up or something.

first i booted with my gparted cd. the boot flag was on the wrong partition so i put it back. i rebooted but still nothing changed. then i used live cd, went sudo mount /dev/hda1 /mnt, opened the fstab and didnt know what to do.

i have heard this is a common problem in edgy?

i would really appreciate it if you could help me. sorry i didnt provide any more detaile information but the live cd freezes every 15 minutes so i dont have time ](*,)

---

### Post by SirPecanGum on 2006-11-03
I had disappearing partitions in Edgy so I removed the UUIDs and all seems to be well now.

---

