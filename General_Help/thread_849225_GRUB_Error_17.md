---
title: "GRUB Error 17"
date: 2008-07-04
forum: General Help
---

### Post by SafariAl on 2008-07-04
So I'm about to go to bed and put Ubuntu in suspend mode, which I don't usually do regularly. Now this morning I woke up and powered it on. GRUB Error 17, my worst nightmare. I have absolutely no idea how to solve this, but I cannot reinstall, there is a game I've been coding for a month on that partition that i cannot lose. Please help me!

---

### Post by lisati on 2008-07-04
Have a look at  [http://ubuntuforums.org/showpost.php?p=5315917&postcount=2](http://ubuntuforums.org/showpost.php?p=5315917&postcount=2)

---

### Post by SafariAl on 2008-07-04
Quick Answer i love it!

I'm getting stuck at
```
find /boot/grub/stage1
```

Error 15 file not found

---

### Post by SafariAl on 2008-07-04
ok, sorry for the double post, im in a bit of a rush and need an answer.
```
sudo mount -t ext3 /dev/sda5 /mnt/root/
```

it tells me:

wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

---

### Post by Frozsyn on 2008-07-04
I think the first thing to do is to save your important work.
If you are using the Ubuntu Live CD, you should be able too mount any working partition with the menu [Places]/[Computer] or directly in the menu [Places]

If your partition is not visible here... I don't know what to think. Maybe it will be time to consider tools that can rescue losted partition...

---

### Post by SafariAl on 2008-07-04
if i can get to my game, I'd be willing to do anything. It's on the desktop on the linux partition (/dev/sda5)

---

### Post by DeathOnJuice on 2008-07-04
> **SafariAl said:**
> ok, sorry for the double post, im in a bit of a rush and need an answer.
```
sudo mount -t ext3 /dev/sda5 /mnt/root/
```

it tells me:

wrong fs type, bad option, bad superblock on /dev/sda5, missing codepage or helper program, or other error. In some cases useful info is found in syslog - try dmesg | tail or so

If you're sure that's the right partition and it is ext3 (I would skip the -t ext3 to be sure), it may be corrupted. Try, however, skipping the find /boot/grub/stage1 step and using (hd0, 4) (yes, that's 4, not 5; counting starts from 0) in the next step.

Best of luck.

---

### Post by SafariAl on 2008-07-04
Well, I got to setup (hd0,0) and received an Error 15 (or 17 can't remember) Drive not mounted. All I really need to do is access that partition to get my game and if there are any other tools to do that, I'll glady use them and reinstall.

---

### Post by ingis on 2008-09-20
Same problem. After suspend got Grub error 17. find /boot/grub/stage1 gets error 15 file not found.

That is what I have find on internet:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/203537)

---

