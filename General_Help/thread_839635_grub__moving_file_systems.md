---
title: "grub : moving file systems"
date: 2008-06-24
forum: General Help
---

### Post by abrazafi on 2008-06-24
Hi All,


I'm running kubuntu 7.10 (K7.10) with 2 hard disks (HD). 
  - the first HD (hda) contains the swap and the /boot
  - the 2nd HD (hdb) contains the /root, /home etc.

I want to use only one HD, instead installing everything, from scratch,
I created a new partion and copied over into the first HD the filesystem's.
In K7.10, in the grub menu/file, the root specification is not anymore
like root=/dev/hda1 but a real partition ID (numerical values).

I tried to add a new entry on the grub menu like this:

kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda4 ro quiet splash

which /dev/hda4 is the new /root, /home, etc.
And the system says that cannot mount the /dev/hda4

question: is there anyway or a grub tool that can display
or giving me the partition ID on a specific HD? Which I can 
put into the grubbmenu then load the /root filessyem from the 
first disk.

Any suggestion will be welcomed.
Thanks,
Abdon.

---

### Post by ibuclaw on 2008-06-24
the command would be

```
sudo blkid /dev/sda4
```
To get the UUID number of the partition.

Then put in your grub menu.lst line:
```
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=**123-YOUR-UUID-NUMBER-321** ro quiet splash
```

Regards
Iain

---

