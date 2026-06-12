---
title: "Erasing your harddrive?"
date: 2008-05-18
forum: General Help
---

### Post by .Scy on 2008-05-18
Would using this program to erase my hard-drive make it so i can install windows XP from ubuntu?

[http://www.aevita.com/eraseharddrive/](http://www.aevita.com/eraseharddrive/)

Because I can't install ubuntu onto my computer, it won't let me type in my password when it starts up.

---

### Post by narhen on 2008-05-18
Not sure I understand ur problem. Can't you install XP or, is it that you can not log in, in Ubuntu?

---

### Post by .Scy on 2008-05-18
both, but i want to reinstall windows though...

---

### Post by narhen on 2008-05-18
You don't need to erase ur HDD, before going back to xp at all. Just make sure you install XP on the same partition you installed Ubuntu. The partition will be formatted before install will begin. (you need to boot up from your XP cd to do this). After installed, you probably will delete ur swap partition.

---

### Post by the8thstar on 2008-05-18
**.Scy**, I already told you about the password not showing up in a diferent thread. Check it and come back here afterwards

---

### Post by Sef on 2008-05-18
Make sure that XP is on the first partition.

---

### Post by .Scy on 2008-05-18
It says xp can't find any harddrives:confused:

---

### Post by Mhurst1 on 2008-05-18
> **.Scy said:**
> It says xp can't find any harddrives:confused:
Is it a SATA Drive? Also what version of XP is it?

---

### Post by .Scy on 2008-05-18
Its built in, HP Pavilion Dv5000

---

### Post by the8thstar on 2008-05-18
If you have the LiveCD, boot it and open a terminal window.

Type: 

> sudo fdisk -l

to list all the partitions on your hard disk.

Paste the results in your next post.

Then we'll see what's going on

---

### Post by .Scy on 2008-05-18
> **the8thstar said:**
> If you have the LiveCD, boot it and open a terminal window.

Type: 



to list all the partitions on your hard disk.

Paste the results in your next post.

Then we'll see what's going on

terminal window? how do i get to that?

---

### Post by the8thstar on 2008-05-18
When you use the LiveCD, do you have a screen with icons on it?

---

