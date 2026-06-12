---
title: "Can't find CD-Drive in ubuntu and windows"
date: 2008-01-20
forum: General Help
---

### Post by Maikelv on 2008-01-20
Hi,

After installing Ubuntu, windows AND ubuntu can't find my cd drive anymore. It worked in Windows before.
I can still boot the livecd, so my drive is not broken.

Any suggestions ?

---

### Post by danwood76 on 2008-01-20
What do you mean you cant find it?
If you insert an audio CD does it do anything?

Is your system a tri-boot or do you only have ubuntu at the moment?

regards,
Danny

---

### Post by Creole on 2008-01-20
He posted this for me, but i've created an account so you can see. I get this message 'mount: special device /dev/scd0 does not exist'. So i can see the icon but when i click i get this message,when i insert a DVD or CD it begins spinning and stops rightaway. I have XP on the first partition and Ubuntu on the second. (although it's the order of installing, before installing ubuntu my drive worked in XP.

---

### Post by danwood76 on 2008-01-20
Hmmm, it could be that there is an error in the symlink /dev/cdrom.

could you please post the result of:
```
 cat /etc/fstab 
```
and
```
 ls /dev/sd* 
```

regards,
Danny

---

### Post by Creole on 2008-01-20
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=fd01ce7b-b153-49cd-aa29-c81a9bdf5f4e /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=02A010A4A0109FE9 /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=d64ed1e8-34ce-4134-893b-9ac55e5aaa8c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0


AND 


/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3

Thanks for your  help.

---

### Post by danwood76 on 2008-01-20
What error message do you get in windows, or does it work in windows?

regards,
Danny

---

### Post by Creole on 2008-01-20
No message at all, it just isnt there, there's no Dvd/Cd icon where it should have been. First time i installed ubuntu it worked fine, no probs at all. But i formatted my pc reinstalling XP and ubuntu my CD drive wasnt there so I again reinstallerd XP and now ubuntu and sees the problem lays some where in ubuntu. Only problem is that i don't know where. I really hope this can be fixed otherwise i can't use Ubun tu anymore and that would be a real shame. Can't even imagine that theres no solution for this problem.

Creole

---

### Post by danwood76 on 2008-01-20
I dont see how installing ubuntu would break your CD drive in windows.
The operating systems are seperate and dont share anything except grub.

This leads me to believe its a hardware problem, have you made any hardware changes / BIOS changes before you did the re install.

You could try re installing both OS's, if you have only just done so to see if it will fix the problem.

regards,
Danny

---

### Post by zipperback on 2008-01-20
> **Maikelv said:**
> Hi,

After installing Ubuntu, windows AND ubuntu can't find my cd drive anymore. It worked in Windows before.
I can still boot the livecd, so my drive is not broken.

Any suggestions ?

Installing Ubuntu would not have any affect on your Windows installation not seeing the CD drive.

Check your hardware connections.

-zipperback
:popcorn:

---

### Post by Maikelv on 2008-01-21
> **zipperback said:**
> Installing Ubuntu would not have any affect on your Windows installation not seeing the CD drive.

Check your hardware connections.

-zipperback
:popcorn:

If the hardware would be broken, It wouldn't be possible to boot from a live cd, right ? Besides that, it worked while only xp was installed. (we reconstructed the setting twice; install windows (cd drive works) , install ubuntu (cd drive doesn't work anymore), format everything and repeat)

My guess is the problem lies in the grub loader, the only thing is, I don't have the slightest clue on how to solve it.

---

### Post by danwood76 on 2008-01-21
install ubutnu then install windows after, check the CD drive and re install grub afterwards from the live CD to see if that makes any difference.

at least that way you will know if grub is messing up your CD drive as it should work after you install XP but not grub if grub is the issue.

You could always use lilo as an alternative or something more lightweight like GAG which is all located in the MBR.

regards,
Danny

---

