---
title: "Setting up grub after reinstallation?"
date: 2007-05-16
forum: General Help
---

### Post by Awake on 2007-05-16
So, here's my situation, I've got 2 hard drives, Windows xp on the master, and Ubuntu edgy on the slave, when I installed Ubuntu I believe I put grub on the master, which is the Windows drive. And now I need to reinstall Windows, so what do I do about grub? How will I be able to boot to Ubuntu after reinstalling Windows?

---

### Post by dcstar on 2007-05-16
> **Awake said:**
> So, here's my situation, I've got 2 hard drives, Windows xp on the master, and Ubuntu edgy on the slave, when I installed Ubuntu I believe I put grub on the master, which is the Windows drive. And now I need to reinstall Windows, so what do I do about grub? How will I be able to boot to Ubuntu after reinstalling Windows?

Search out the forum HOWTOs on reinstalling Grub.

---

### Post by Awake on 2007-05-16
That might be crazy enough to work...

---

### Post by aquavitae on 2007-05-16
I suggest after instaling windows, make your ubuntu drive master, and install grub on it instead.  Then map the drives in grub's menu.conf.  I think the code is something like
map (hd0), (hd1)
map (hd1), (hd0)
but its some time since I've done it so I can't quite remember.  I've found in the past that insalling grub on the windows drive can mess up the windows installation, and of course if you have to reinstall windows you have to reinstall grub (as you've found out :))

As dcstar says, there's plenty of guides on installing grub on the internet.

---

