---
title: "Bungled chmod on file sudoers"
date: 2007-05-11
forum: General Help
---

### Post by dachinster on 2007-05-11
Hi guys,
i was trying to change permissions on the sudoers file because i could not save some changes i made to it (i was trying to allow firestarter to run all the time without me having to start it manually or by using a terminal sudo command but i botched it)

> dachinster@Ubuntu:/etc$ sudo chmod -cfRv + rwx sudoers
Password:
chmod: cannot access `rwx': No such file or directory
failed to change mode of `rwx' to 0403 (r------wx)
mode of `sudoers' retained as 0440 (r--r-----)
dachinster@Ubuntu:/etc$ sudo chmod -cfRv + -rwxr-xr-x sudoers
chmod: cannot access `+': No such file or directory
failed to change mode of `+' to 0403 (r------wx)
mode of `sudoers' changed to 0000 (---------)
dachinster@Ubuntu:/etc$ sudo chmod -cfRv + rwx sudoers
sudo: /etc/sudoers is mode 00, should be 0440
dachinster@Ubuntu:/etc$ sudo chmod -cfRv + rwx sudoers
sudo: /etc/sudoers is mode 00, should be 0440


now i cant start firestarter at all

---

### Post by taurus on 2007-05-11
Boot into recovery mode from GRUB menu and run

```
chmod 440 /etc/sudoers
```

---

### Post by dachinster on 2007-05-11
this actually worked quite well.. thanks!

---

