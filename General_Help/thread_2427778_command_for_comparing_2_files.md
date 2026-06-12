---
title: "command for comparing 2 files"
date: 2019-09-26
forum: General Help
---

### Post by satimis on 2019-09-26
Hi all,

Ubuntu 16.04

Which command shall I run to compare 2 grub.cfg files for finding out the difference?

Thanks

Regards
satimis

---

### Post by deadflowr on 2019-09-26
diff
generically like
```
diff one-file the-other-file
```
graphically you can install and use meld.

diff's installation package (diffutils) is required on Ubuntu so already installed, meld would need to be installed.

```
man diff
``` 
for more options.

---

### Post by mc4man on 2019-09-26
In some cases I like to use the patch format with diff. It'll create a by line number text file showing how to turn filename 1 into filename 2.
Easy to read and view changes.
```
diff -Naur  filename1 filename2 > whatever.patch
```
If wanting to see how to turn file2 into file1 just reverse order in command.

---

### Post by The Cog on 2019-09-26
Personally, I would use meld. And if there's no GUI on the machine in question, I would copy the files back to a machine that does have a GUI, and then use meld.

---

### Post by satimis on 2019-09-26
Hi all,

Lot of thanks for your advice.

I have been struggling sometimes to sort out the dual-boot problem on my daily working PC, say PC-1.  It always boots drive-1 even selecting to boot drive-2.

PC-2 is a spare desktop PC which supports triple-boot without problem.  I'm prepared to compare /boot/grub/grub.cfg of 2 PCs in anticipation to find out their difference.

Copied /boot/grub/PC-2_grub.cfg to PC-1

On PC-1 terminal run;```

&#10219; diff -Naur PC-2_grub.cfg /boot/grub/grub.cfg > grub_cfg.patch

```

My findings are```

-insmod part_gpt	#PC-2
+insmod part_msdos	#PC-1
 insmod lvm
 insmod ext2

-	set root='hd1,gpt2'	#PC-2
+	set root='hd0,msdos1'	#PC-1

.....

```

I wonder whether changing```

+insmod part_msdos

```
to;
```

+insmod part_gpt

```

and```

+	set root='hd0,msdos1'

```
to;
```

+	set root='hd0,gpt2'

```

can help me out ?

Advice would be appreciated.

Regards
satimis

Remark: I'm not allowed to upload grub_cfg.patch here

---

### Post by SeijiSensei on 2019-09-26
Why not just swap the SATA cables on PC-1?

---

### Post by satimis on 2019-09-26
> **SeijiSensei said:**
> Why not just swap the SATA cables on PC-1?
Hi,

Thanks for your advice.

I did it before without result.  I'm very surprised.  If both drive-1 and drive-2 connected I can only boot drive-1.  Booting drive-2 it will automatically boot drive-1 finally.  To boot drive-2 I have to disconnect drive-1.

Please see my another posting;
[ubuntu] Dual boot fails
[https://ubuntuforums.org/showthread.php?t=2426561&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2426561&highlight=satimis)

Thanks

satimis

---

### Post by Dennis N on 2019-09-26
> I wonder whether changing...
One computer is using BIOS (or UEFI in compatability mode), since it boots msdos partitioned disk. The other disk is GPT, which could be a UEFI system. The changes are not a good idea since the commands are specific to disk type. Probably you will get some error on booting (or failure to boot).

---

### Post by satimis on 2019-09-26
> **Dennis N said:**
> One computer is using BIOS (or UEFI in compatability mode), since it boots msdos partitioned disk. The other disk is GPT, which could be a UEFI system. The changes are not a good idea since the commands are specific to disk type. Probably you will get some error on booting (or failure to boot).
Hi,

Thanks for your advice.

My next attempt will be connecting a spare SSD-128G to replace drive-2 and install Ubuntu 18.04 on it to see whether I can sort out dual-boot problem.

I suspect my problem was caused when I installed Ubuntu 16.04 on drive-1, drive-2 was disconnected.  Please see my posting mentioned on my previous posting.
[ubuntu] Dual boot fails
[https://ubuntuforums.org/showthread.php?t=2426561&highlight=satimis](https://ubuntuforums.org/showthread.php?t=2426561&highlight=satimis)

---

### Post by TheFu on 2019-09-26
diff
sdiff
meld
tkdiff

I don't dual boot. Too much hassle. Use virtualization. Much easier. Fewer risks.

---

### Post by satimis on 2019-09-26
> **TheFu said:**
> diff
sdiff
meld
tkdiff

I don't dual boot. Too much hassle. Use virtualization. Much easier. Fewer risks.
Thanks for your advice.

I'm also running virtualization and container but keeping the host clean only for running them.  However for graphic and video editing I need to do it on host for such a reason I need dual boot.  That drive will be solely for graphic and video editing.

satimis

---

