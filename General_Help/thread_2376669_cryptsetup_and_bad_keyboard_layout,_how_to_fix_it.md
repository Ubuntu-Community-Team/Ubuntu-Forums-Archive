---
title: "cryptsetup and bad keyboard layout, how to fix it?"
date: 2017-11-04
forum: General Help
---

### Post by Grummfy on 2017-11-04
Hello,
I recently install ubuntu 17.10. Like I do several times with the previous version I have activated the encryption of the disk.
Unfortunately, the keyboard layout chosen is qwerty instead of the one I used, and I see no way to change it.

So anybody have a tip to fix it ?

thanks

---

### Post by TheFu on 2017-11-05
Heard on a respected podcast that the only supported keyboard for FDE in 17.10 is English. I looked for a bug report about this and didn't see it.

It might be possible to boot with 1 userid (English keyboard), then logout and login using a different account that has whatever keyboard/mapping you want as a work around. Just a thought. I haven't tested it.

Sorry I don't have any better option.

---

### Post by Grummfy on 2017-11-07
the issue is booting th computer, before the session manager ;)

---

### Post by ecormier on 2018-02-07
It's a bug, the report is here: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1719612](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1719612)

The temporary work around is:
sudo ln -s /etc/console-setup/cached_UTF-8_del.kmap.gz /etc/console-setup/cached.kmap.gz
sudo update-initramfs -u

---

### Post by Grummfy on 2018-02-07
thanks for it

---

### Post by Grummfy on 2018-02-07
thanks for it

---

