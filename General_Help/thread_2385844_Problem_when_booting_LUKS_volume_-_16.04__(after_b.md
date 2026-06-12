---
title: "Problem when booting LUKS volume - 16.04  (after boot-repair)"
date: 2018-02-25
forum: General Help
---

### Post by expat778877 on 2018-02-25
Hi - I have 16.04 LTS dual booting with Windows 10 on a Dell Inspiron laptop.  It worked great until a recent grub update, which made the grub menu disappear.   This took another forum thread to resolve ([https://ubuntuforums.org/showthread.php?t=2385201&highlight=boot-repair](https://ubuntuforums.org/showthread.php?t=2385201&highlight=boot-repair)  -  Thanks oldfred!)

Now I can see the grub menu again, but can't get past the 'unlock' function when booting Ubuntu (after entering the passphrase, I see "cryptsetup: cryptsetup failed, bad password or options?").   I know this password is OK because I can boot a 16.04 live USB and mount the volume from the files and disks utilities.

Any ideas?

---

### Post by georgeskesseler on 2018-02-25
Maybe the keyboard layout is wrong, And so "MyPassword" becomes "MzPassword" or some other gibberish.

---

### Post by expat778877 on 2018-02-26
How do I tell which keyboard layout is configured?

---

### Post by expat778877 on 2018-03-01
Anyone have an idea on how I can resolve this?

---

