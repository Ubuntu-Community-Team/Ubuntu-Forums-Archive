---
title: "Dual Boot problem"
date: 2007-06-25
forum: General Help
---

### Post by krityx on 2007-06-25
ok, so here's the problem
I first installed Windows server 2003 . then I installed windows XP on another partition, but same HDD. Yesterday I tried to install Ubuntu, so I formated the win XP partition and installed ubuntu on that partition. the installation went well but when i restarted at the end, the bootloader was MBR and it showed me Win XP and Win 2003 ?  and I couldnt enter any of them. It said that the file ntoskrnl.exe was missing from windows root/system32, so i had to reinstall XP to get 2003 working again.
I think I need to overwrite that bootloader with GRUB or whatever ubuntu uses. How do I do that? 
Thanks.

---

### Post by r0ck80y on 2007-06-25
> **krityx said:**
> ok, so here's the problem
 I formated the win XP partition and installed ubuntu on that partition...... so i had to reinstall XP to get 2003 working again.

You reinstalled winXP on the ubuntu partition? I mean, did you remove ubuntu?

---

### Post by krityx on 2007-06-25
yup removed it , then installed win xp so that i could access win 03 which is my main OS.
i want to keep win 03 + ubuntu thats all, but it seems i cant get rid of the ******* xp !

---

### Post by r0ck80y on 2007-06-25
You need to install ubuntu again. The installer itself creates the grub menu with the ubuntu boot-up options. Cant say exactly why the grub menu wouldn't appear after ubuntu installation if you say it went off well. Try again and let us know. Try pressing ESC after the bios screen...maybe the grub menu appears then.

---

### Post by krityx on 2007-06-25
its useless, 'cause before ubuntu i tried to install suse, and kinda the same thing happened. the GRUB from suse appeared and if i chose suse it would work but if i were to choose windows it would take me to MBR where i was supposed to choose between win 03 an XP (which was deleted). i didnt know that it's possible to have 2 bootloaders. so that's the problem, i cant properly remove win XP because MBR was installed by WIN xp. so if i could remove win XP and its MBR it would all work fine. 
i ran windows+linux a lot of times before, with no problems. 
do you know where windows installs it's MBR ? so that i can overwrite the MBR with GRUB ? i think that's the only possible solution availaible for me.

thanks for taking the time to reply !

---

### Post by r0ck80y on 2007-06-25
Can you post your disk partitions?
```
 fdisk -l 
```

---

### Post by krityx on 2007-06-25
fdisk -l does nothing ...

---

### Post by r0ck80y on 2007-06-25
Boot into live CD and open terminal. Type "sudo su". This makes you live-CD root. Now type "fdisk -l".

---

### Post by krityx on 2007-06-25
now it worked. i wasnt root.
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        2611    20964825    f  W95 Ext'd (LBA)
/dev/sdb2   *        2612       28991   211897350    7  HPFS/NTFS
/dev/sdb3           28992       30400    11317792+   7  HPFS/NTFS
/dev/sdb5               2        2611    20964793+   7  HPFS/NTFS

```

---

### Post by r0ck80y on 2007-06-25
Can you tell me what is the scheme of your installation? Where are the windows OSs present and where you want to install ubuntu?

P.S I may not be able to reply soon, my net connection's going down :(

---

### Post by krityx on 2007-06-25
sure.
160 GB HDD - 1 partition-stock(no OS)
250GB HDD - 3 partitions
1) 200 GB - stock
2) 20 gb - win 2003
3) 10 gb - win Xp - where i want to install ubuntu

---

### Post by r0ck80y on 2007-06-25
I have not used windows for quite a while now, so i'll try to be as accurate as possible.
Remove XP. Boot using win 2003 CD. Now you have to replace the windows XP MBR with the Server one. I hope you know how to fix the MBR because i vaguely remember. I think you gotta enter the recovery console (pressing 'r' or 'c' ) and at the DOS command prompt enter "fixmbr" or "fixboot" (both commands work). This restores the win 2003 MBR and your computer will directly boot into it. Now install ubuntu in the appropriate partition which will replace windows 2003 MBR with grub. If the windows entry is not there in the menu, you can boot into your installed ubuntu system and edit the /boot/grub/menu.lst file.
Good luck :P

---

### Post by krityx on 2007-06-25
great. that's what i'm looking for. 
i can't thank you enough for taking your time to help me, and answer so fast !
:KS:KS:KS:KS

---

