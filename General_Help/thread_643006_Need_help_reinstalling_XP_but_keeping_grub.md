---
title: "Need help reinstalling XP but keeping grub"
date: 2007-12-17
forum: General Help
---

### Post by general.chaos on 2007-12-17
I am currently dual booting XP and Ubuntu 7.10.

Yesterday XP crapped the bed, and now it needs reinstalled. How can I do this without blowing out my bootloader. When I am done installing I want to still be able to access Ubtuntu. I know XP formats your MBR, but there has to be a way to back that up and restore it via a live cd.

Any help would be appreciated!

Thanx!

---

### Post by danwood76 on 2007-12-17
Its not actually possible, XP will always overwrite the MBR, I think its microsofts way of pissing off anyone who dual boots.
Vista is the same also.

Theres and easy way round it though, your grub is installed in /boot, all you need to do is once you have redone xp just boot up the live CD chroot to your linux partition and reinstall grub on the MBR.

There are guides around if you need them,

---

### Post by general.chaos on 2007-12-17
found this guide:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

thanks!

---

### Post by iKonaK on 2007-12-17
dump xp, is rubbish :) and vista too...

---

### Post by danwood76 on 2007-12-17
Very true, I only use vista for gaming, all other tasks can be completed with better results under linux.

---

### Post by general.chaos on 2007-12-17
I use XP primarily for gaming...

Why is it any time I come here looking for help someone always tells me to drop whatever version of Windows I am running at the time?   I know you like your OS and all, but I came here for help, not to hear a Linux elitist tell me what OS** I need** to use.

---

### Post by Slim Odds on 2007-12-17
> **general.chaos said:**
> .....but I came here for help, not to hear a Linux elitist tell me what OS** I need** to use.

They are not telling what OS you need, they're telling you what OS **you want**.   

:lolflag:

---

### Post by general.chaos on 2007-12-17
in any regard, I often wish people wouldn't push their OS on other people.  

O well, I'm out, thanx to those who were actually helpful!

---

### Post by iKonaK on 2007-12-17
general.chaos, after your last posts i find myself in position to give you a reply,
at an earlier post i suggested you to dump xp/vista,
i wanna assure you that that was a personal suggestion, i don't hate win or anything but i find terribly irritating to be forced to reinstall win after less then a week because of the lagging. i never encountered a major problem in linux/ubuntu and i was pointing the obvious.. but fell free to do whatever you want, that's the beauty, is your choice based on your opinions whatever you do with your machine...

---

### Post by Lostincyberspace on 2007-12-17
I reinstall both all the time since I like to play with the system files to see what I can get away with and Linux is much easier to do.

---

### Post by danwood76 on 2007-12-17
> **general.chaos said:**
> 
Why is it any time I come here looking for help someone always tells me to drop whatever version of Windows I am running at the time? 

The simple reason is windows is the most unstable operating system, it is only good if you like gaming.
Every task that the normal PC user uses a computer for can be carried out in linux.

And I wasnt telling you you need to dump XP as I myself use vista for gaming, that would be rather hypocrytical of me :)

---

### Post by general.chaos on 2007-12-17
> **iKonaK said:**
> general.chaos, after your last posts i find myself in position to give you a reply,
at an earlier post i suggested you to dump xp/vista,
i wanna assure you that that was a personal suggestion, i don't hate win or anything but i find terribly irritating to be forced to reinstall win after less then a week because of the lagging. i never encountered a major problem in linux/ubuntu and i was pointing the obvious.. but fell free to do whatever you want, that's the beauty, is your choice based on your opinions whatever you do with your machine...

If you're only using it for gaming then there would be no lagging over time.

Thanks for clearing that up though!

---

### Post by Lostincyberspace on 2007-12-17
You can also use the super grub boot disk to reset the mbr and if you are reinstalling completely then it should not require any tweaking to make it work right after words.

---

