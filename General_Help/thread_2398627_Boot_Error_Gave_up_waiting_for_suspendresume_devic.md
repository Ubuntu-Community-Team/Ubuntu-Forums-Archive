---
title: "Boot Error: Gave up waiting for suspend/resume device, root device--Ubuntu 18.04"
date: 2018-08-15
forum: General Help
---

### Post by szkieletor on 2018-08-15
Hi,

I updated Ubuntu to 18.04 LTS from 16.04 LTS and right after that the boot problem happens.

Then I run boot-repair and the surroundings slightly changed, but still Ubuntu cannot boot. If I choose "Ubuntu" in GRUB2, violet-color screen with no text hangs, and no going forward.

This is the Boot info: [https://pastebin.ubuntu.com/p/HvCx9jrfRF/](https://pastebin.ubuntu.com/p/HvCx9jrfRF/)

Now I tried to boot Ubuntu by recovery mode, but it stops during boot sequence, with the message following:

[HTML]
Gave up waiting for suspend/resume device
Done.
Begin: Waiting for root file system device. 
Gave up waiting for root device. Common problems: 
  -Boot args (cat /proc/cmdline) 
    -Check rootdelay= (did the system wait long enough?)
  -Missing modules (cat /proc/modules; ls /dev) 
ALERT! UUID=246585c1-7fa9-4ccd-awaw-ef358267b93a does not exist. Dropping to a shell!
[/HTML]

Then initramfs shell started.

Also, I have a ACPI error message before that.

What should I do in this case?
Although there are a bunch of threads regarding the same error message and I tried many commands raised there, the problem have not resolved.

/dev/sda7 is the partition installed Ubuntu, /dev/sda3 is EFI partition for boot, /dev/sda8 is swap partition.

[HTML]lsblk -f
NAME   FSTYPE   LABEL            UUID                                 MOUNTPOINT
loop0  squashfs                                                       /rofs
sda                                                                   
&#9500;&#9472;sda1 vfat     SONYSYS          DC5A-D06B                            
&#9500;&#9472;sda2 ntfs     Windows RE tools 52BE5F7BBE5F5717                     
&#9500;&#9472;sda3 vfat                      48B2-EB1D                            
&#9500;&#9472;sda4                                                                
&#9500;&#9472;sda5 ntfs                      01D18A3AE79E42E0                     
&#9500;&#9472;sda6 ntfs     Recovery         0CBE6577BE655A6A                     
&#9500;&#9472;sda7 ext4                      246585c1-7fa9-4ccd-a2a2-ef358367b93a 
&#9492;&#9472;sda8 swap                      b38f5a65-67a8-4667-899c-dd482815a59f [SWAP]
sdb                                                                   
&#9492;&#9472;sdb1 vfat                      00E2-7946                            /cdrom
sr0                                                                   
zram0                                                                 [SWAP]
zram1                                                                 [SWAP]
zram2                                                                 [SWAP]
zram3                                                                 [SWAP]

lubuntu@lubuntu:~$ blkid

/dev/sda1: LABEL="SONYSYS" UUID="DC5A-D06B" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="f2b3e73e-9dec-40cf-834f-7ad4a2ec02c8"
/dev/sda2: LABEL="Windows RE tools" UUID="52BE5F7BBE5F5717" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="49223721-c333-4631-980f-97a7a233991d"
/dev/sda3: UUID="48B2-EB1D" TYPE="vfat" PARTLABEL="EFI system partition" PARTUUID="ea9ae731-6efa-4542-ab70-ef86cbdadefe"
/dev/sda5: UUID="01D18A3AE79E42E0" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="5ead2b50-5129-409d-832b-825e00c085ce"
/dev/sda6: LABEL="Recovery" UUID="0CBE6577BE655A6A" TYPE="ntfs" PARTLABEL="Basic data partition" PARTUUID="8ab407a1-1f7f-4cd0-a052-4ddf8960e0d7"
/dev/sda7: UUID="246585c1-7fa9-4ccd-a2a2-ef358367b93a" TYPE="ext4" PARTUUID="4f231295-b629-44ab-8e6e-69343ea4621a"
/dev/sdb1: UUID="00E2-7946" TYPE="vfat"
/dev/loop0: TYPE="squashfs"
/dev/sda8: UUID="b38f5a65-67a8-4667-899c-dd482815a59f" TYPE="swap" PARTUUID="39dc0eab-6ea1-442b-bcb6-cb9980eda8ec"
/dev/zram0: UUID="3d3dbf2f-04d2-4dd1-8374-15e318f22384" TYPE="swap"
/dev/zram1: UUID="5376af07-b6b4-41ac-9c21-c6fb5f2cb269" TYPE="swap"
/dev/zram2: UUID="05fc722e-efe1-43d7-87c5-c9971707e19a" TYPE="swap" /dev/zram3: UUID="e639c241-012d-41a3-b9ef-00131fe85d80" TYPE="swap"
[/HTML]

---

### Post by Bashing-om on 2018-08-15
szkieletor; Uh Huh ..

The system is not lying to you: 
> 
ALERT! UUID=246585c1-7fa9-4ccd-awaw-ef358267b93a does not exist.

blkid reports the correct UUID : 246585c1-7fa9-4ccd-a2a2-ef358367b93a .
compare:
246585c1-7fa9-4ccd-awaw-ef358267b93a
246585c1-7fa9-4ccd-a2a2-ef358367b93a
where the 1st is in error, maybe you fat fingered the /etc/fstab file ?

Show us the - sda7 - /etc/fstab file:
```

cat /etc/fstab

```

[INDENT][INDENT]sounds likely to me
[/INDENT][/INDENT]

---

