---
title: "wubi installed, now it wont work"
date: 2007-07-11
forum: General Help
---

### Post by redsunx on 2007-07-11
Well went well on the install rebooted hit ubuntu and i got some codes on the bottom the cursor hangs after it says linux/interg or something similar so what now?

---

### Post by ago on 2007-07-11
Have a look into /tmp/lupin.log and /tmp/zenigata.log for any message about problems mounting, you can use the "more" command to read the files

---

### Post by redsunx on 2007-07-11
I cant find a tmp folder anywhere

---

### Post by ago on 2007-07-11
what do you see when you run ls? (it's LS lower case)

---

### Post by redsunx on 2007-07-11
Nothing it gets past grub everything then i assume it starts loading the kernel and then hangs hd not in use cpu temps are at 28c wich means its idle ram is idle to i cant figure it out, Ubuntu is the only distro ive had problems with

---

### Post by ago on 2007-07-12
remove "quite splash" from c:\wubi\boot\grub. Also try to boot the livecd.

---

