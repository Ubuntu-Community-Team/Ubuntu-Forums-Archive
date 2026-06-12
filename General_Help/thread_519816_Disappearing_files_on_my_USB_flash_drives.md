---
title: "Disappearing files on my USB flash drives?"
date: 2007-08-07
forum: General Help
---

### Post by baz.g on 2007-08-07
ok, so i have searched on these forums about the magic disappearing files on my hard drive and have solved my immediate problem by running these commands prior to removing the usb drive:

[code]
sudo sync

sudo umount /dev/sda1 (or whichever device)
[/sudo]

as suggested by funchords in another related post. my question now is why are the files being buffered? and do i have to do this sync command every time i want to transfer anything to my usb flash drives?

many thanks in advance :)

Baz

---

