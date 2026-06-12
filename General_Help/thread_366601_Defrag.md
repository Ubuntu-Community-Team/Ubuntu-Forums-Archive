---
title: "Defrag"
date: 2007-02-21
forum: General Help
---

### Post by Rhaddad on 2007-02-21
Hello,
I think its about time i defrag my files but i cannot find a utility to do so. 
And if i do not need to can some one explain why.

---

### Post by anaconda on 2007-02-21
you dont need to do that, because ext3 filesystem doesn't fragmentate very easily. I think this is because of the journaling.

but if you want to check your filesystem for errors you can run
sudo fsck -f /dev/diskname
where diskname is the partition you want to check.. eg. hda1, hda2, sda1  or sda2  I think this  mentions the fragmentatiton procentage.. And it is adviced that fsck is done to unmounted filesustem. so it is best done from the liveCD.

inn synaptic there is also a program called defrag, but I think it is for ext2 filesystems..

---

### Post by lukew on 2007-02-21
> **anaconda said:**
> you dont need to do that, because ext3 filesystem doesn't fragmentate very easily. I think this is because of the journaling.

but if you want to check your filesystem for errors you can run
sudo fsck -f /dev/diskname
where diskname is the partition you want to check.. eg. hda1, hda2, sda1  or sda2  I think this  mentions the fragmentatiton procentage.. And it is adviced that fsck is done to unmounted filesustem. so it is best done from the liveCD.

inn synaptic there is also a program called defrag, but I think it is for ext2 filesystems..

There is a defrag tool in the repos. EXT3 should not need defraging, as long as you keep a reasonable chunk of your hd free.


Luke

---

### Post by paparucino on 2007-02-21
> **lukew said:**
> There is a defrag tool in the repos. EXT3 should not need defraging, as long as you keep a reasonable chunk of your hd free.


It should have to be performed automagically at boot time every 30 days.

---

### Post by Spr0k3t on 2007-02-21
I thought it was every thirty boots and not every thirty days.

---

### Post by paparucino on 2007-02-21
> **Spr0k3t said:**
> I thought it was every thirty boots and not every thirty days.
Yeah! You are right! I was confused. I boot the machine every day :-)

---

### Post by lukew on 2007-02-21
> **paparucino said:**
> It should have to be performed automagically at boot time every 30 days.

That does a fsck and not a defrag. fsck checks for sector errors and inconsistencies and not repairs fragmentation of the hd.

Luke

---

### Post by Spr0k3t on 2007-02-21
> **paparucino said:**
> Yeah! You are right! I was confused. I boot the machine every day :-)

Ever since I made my wife build her own computer, I haven't had a need to reboot yet.  Going on day number 28.

---

### Post by Ramses de Norre on 2007-02-21
> **Spr0k3t said:**
> Ever since I made my wife build her own computer, I haven't had a need to reboot yet.  Going on day number 28.

Not really environment friendly...

---

### Post by gruffy-06 on 2007-02-21
I thought file systems in GNU/Linux automatically defragment themselves.

---

### Post by nereid on 2007-02-21
> **Spr0k3t said:**
> I thought it was every thirty boots and not every thirty days.

fsck will run every 30 boots or every 30 days depending on what comes first (you can change the values but you should only do this to an unmounted partition, this means you have to boot with a boot disk).

---

### Post by paparucino on 2007-02-21
> **Spr0k3t said:**
> Ever since I made my wife build her own computer, I haven't had a need to reboot yet.  Going on day number 28.
My pc is ruomrous and during the night I save energy :-)

---

### Post by Spr0k3t on 2007-02-22
> **Ramses de Norre said:**
> Not really environment friendly...

I planted a tree this week and painted my case green... will that work?

---

### Post by jongkind on 2007-02-22
Pyfragtools work for me: [http://ubuntuforums.org/showthread.php?t=169551]("http://ubuntuforums.org/showthread.php?t=169551")

---

### Post by James- on 2007-02-22
> **Spr0k3t said:**
> Ever since I made my wife build her own computer, I haven't had a need to reboot yet.  Going on day number 28.
hahaha major diffrence between linux and windows :) almost never need to reboot :D

---

