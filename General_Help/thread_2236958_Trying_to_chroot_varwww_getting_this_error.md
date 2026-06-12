---
title: "Trying to chroot /var/www getting this error"
date: 2014-07-29
forum: General Help
---

### Post by waloshin on 2014-07-29
chroot: cannot change root directory to 777: No such file or directory

---

### Post by 3rdalbum on 2014-07-30
You're trying to change permissions of /var/www? You are looking for chmod, not chroot.

I strongly recommend you do not change the permissions of /var/www. You would be just making it easier for any attacker to completely own your computer. Very bad.

If you want to put files into /var/www, do it with *sudo*. It's the correct way and it's a lot safer and more secure. Either do the copy direct on the terminal:

```
sudo cp <drag source file in here> /var/www/
```

Or open a root file browser to do the copying in the GUI:

```
gksudo nautilus
```

---

