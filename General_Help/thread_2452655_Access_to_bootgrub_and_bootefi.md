---
title: "Access to /boot/grub and /boot/efi"
date: 2020-10-26
forum: General Help
---

### Post by helen314 on 2020-10-26
```

https://unix.stackexchange.com/questions/524622/what-is-the-relation-between-uefi-and-grub

```

The above reference touches on relations between grub and efi. 
The relation between grub (file) and grub,cfg are known. 

The relation between system UEFI (firmware) and efi - starting  with EFI  partitions are somewhat 
foggy. 

**My questions are:** 
1. why /boot/grub contents is fully accessible and /boot/efi  is not?
2. What Linux security is in jeopardy , therefore  "permission" to access is denied ?
3. How do I bypass this "security" without screwing things up ?

Note 
This is a single user , ME, system no community access is involved.


```

a@a-desktop://boot$ ls
config-4.15.0-120-generic      memtest86+.elf
config-4.15.0-122-generic      memtest86+_multiboot.bin
efi                            System.map-4.15.0-120-generic
grub                           System.map-4.15.0-122-generic
initrd.img-4.15.0-120-generic  vmlinuz-4.15.0-120-generic
initrd.img-4.15.0-122-generic  vmlinuz-4.15.0-122-generic
memtest86+.bin
a@a-desktop://boot$ 

```


When answering a question please:
		    
[LIST]
[*]Read the question carefully and try to answer "the question" , not to explain how the world was created. .
[*]Understand that English isn't everyone's first language so be lenient of bad 			spelling and grammar.
[*]If a question is poorly phrased then either** ask for clarification, ignore it,** or** 			edit the question** and fix the problem. Insults are not welcome.
[*][COLOR=#ff0000]**Don't tell someone to read the manual.**[/COLOR]** Chances are they have and don't get it.                 Provide an answer or move on to the next question**.
[/LIST]
 		    Let's work to help, not to make the original poster feel stupid.

---

### Post by oldfred on 2020-10-26
1 Secuity
2. Windows formats like FAT32 & NTFS allows everyone to write into system. Mount of Windows type partitions is default for all files. Linux sets ownership & permission by file, so access can be limited and some script in a spreadsheet or word doc cannot modify it.
3. So for improved security it is changed. I do change mine back to older setting to allow use, now, but may change again to 0077.

14.04 fstab entry defaults allows access
UUID=FD76-E33D  /boot/efi       vfat    defaults        0       1
16.04 & later  fstab entry umask=0077 totally restricts access
UUID=68CD-3368  /boot/efi       vfat    umask=0077      0       1

I found the standard remount after editing fstab, does not immediately give access.
I have had to reboot.

sudo nano /etc/fstab
Also add noatime (SSD or flash drive)) or relatime(HDD)
#Typical fstab entry:
UUID=d65e4ad3-6315-4838-97a1-ec574cb8575f / ext4 noatime,errors=remount-ro   0       1
#UUID=D966-440A  /boot/efi       vfat    umask=0077      0       1
UUID=D966-440A  /boot/efi       vfat    defaults      0       1
tmpfs /tmp tmpfs defaults,noatime,mode=1777 0 0
# confirm entries work, if just return then ok
sudo mount -a

---

