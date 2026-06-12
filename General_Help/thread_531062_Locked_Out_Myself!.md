---
title: "Locked Out Myself!"
date: 2007-08-21
forum: General Help
---

### Post by pelagic on 2007-08-21
I've just deleted my own user account and created another one to replace it. Unfortunately I didn't give it the ability to use sudo. So I'm out of the game!

The installation is on a Laptop that has no CD slot (or to be more precise: it has either a CD slot or a second HD with (this) Ubuntu but not both at a time!).

I have difficulties to just reinstall the whole thing. The initial installation was made using a USB stick to boot from. But this doesn't seem to work anymore, probably because I've overwritten the MBR on the first HD (which is XP) during the Ubuntu installation.

Any ideas?
Thanks for any hint!

---

### Post by eggdeng on 2007-08-21
Just boot in recovery mode, this logs you in as root and you can create all the user accounts you want.

---

### Post by kellemes on 2007-08-21
> **pelagic said:**
> I've just deleted my own user account and created another one to replace it. Unfortunately I didn't give it the ability to use sudo. So I'm out of the game!

The installation is on a Laptop that has no CD slot (or to be more precise: it has either a CD slot or a second HD with (this) Ubuntu but not both at a time!).

I have difficulties to just reinstall the whole thing. The initial installation was made using a USB stick to boot from. But this doesn't seem to work anymore, probably because I've overwritten the MBR on the first HD (which is XP) during the Ubuntu installation.

Any ideas?
Thanks for any hint!

About sudo, you can add yourself to the sudoers file [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch09_:_Linux_Users_and_Sudo).

---

### Post by pelagic on 2007-08-21
Thanks to eggdeng and kellemes! I'm in again ...
/pelagic

---

### Post by bapoumba on 2007-08-21
> **pelagic said:**
> Thanks to eggdeng and kellemes! I'm in again ...
/pelagic
Just a side note, as you have solved this. On Ubuntu, for a user to have admin privileges, just put the user_login in the admin group ;)

---

### Post by pelagic on 2007-08-21
Yeah, that's exactly what I've done after booting in recovery mode:
usermod -a -gadmin myusername 

Thanks anyway!
/pelagic

---

