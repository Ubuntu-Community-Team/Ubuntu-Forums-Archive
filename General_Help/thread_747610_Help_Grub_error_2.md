---
title: "Help? Grub error 2"
date: 2008-04-06
forum: General Help
---

### Post by Qazoo on 2008-04-06
I really have no idea what I was doing and tried to install unbuntu, I think I installed over windows xp and now unbuntu wont even boot(grub error 2). im just screwing up all over. can anyone help? :(

---

### Post by Qazoo on 2008-04-06
?

---

### Post by pspfreak101 on 2008-04-06
try this on the live cd and open up the terminal

```
sudo grub
find /boot/grub/stage1
it should give you something like (hd0,2)
then do root (hd0,%) --% is the number is gave you in the command above
it should give back something like this "Filesystem type is ext2fs, partition type 0x83"
Finally do this command setup (hd0)
then quit and restart and your done 

```

---

### Post by Qazoo on 2008-04-06
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.
Unknown partition table signature

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,0)
grub> 

hd0,0? normal?

---

### Post by Qazoo on 2008-04-06
grub> root (hd0,0)
root (hd0,0)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
grub> quit


did that and when i restart i still get grub error 2

---

