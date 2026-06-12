---
title: "Booting only XP without installing ubuntu on HDD"
date: 2008-06-15
forum: General Help
---

### Post by enli on 2008-06-15
Hello ,

I just brought new 250GB SATA and i m facing unique situation. I already have Ubuntu+XP installed on HDD1 (sata) and also grub working nicely.

What i m trying to do is whenever i remove my HDD1 (160GB and it has grub in MBR ) and connect only HDD2 (250GB having only XP it should boot it. As you have probably guessed i could just reinstall grub from livecd or from ubuntu on hdd1, grub wont boot. So i made a new ext3 partition on HDD2 and copied image files for grub from livecd to partition /dev/sda5 which is at the start of extented parition after the XP partition.

I have tried the following procedures:
1.booted livecd
2.mounted the partition /dev/sda5 at /media/disk
3.copy whole contents of grub image directory from /usr/share/lib/grub/i386/ to /media/disk/boot/grub/
4.at terminal:
  sudo grub-install --root-directory=/media/disk hdd0
5.it then installed the grub to mbr 
6.made menu.lst in /media/disk/boot/grub/ and added the following lines
```

timeout 5
title Windows XP
rootnoverify (hd0,4)
chainloader +1
makeactive
savedefault

```
note: grub told that it found stage1 files at (hdd0,4) when tried by          find /boot/grub/stage1
7.unmounted /media/disk/
8.reboot

Now it shows the grub menu selection and after timeout it just stops showing message " Starting up..." .Nothing happens afterwards and i have to reboot

Another procedure:
1. booted to livecd
2. terminal >> sudo grub
3. at the grub shell :
   find /boot/grub/stage1            (found at (hd0,4))
   root(hd0,4)
   setup(hd0)
   quit
4.reboot

Grub menu list shows up but cant get past the "Starting up" screen.

Now you might say why i m trying to get grub working on a HDD having only XP and not using XPs bootloader ? 
Cause i want to have a nice boot menu with sexy splashimage :D

I m not at home so it might take a day to come back and reply.
Any thoughts ?

Many thanks
EnLi

EDIT: I would also like to add option to boot my other OSes on another hdd, i guess i will just have to edit my menu.lst and change hd0 to hd1 right ?

---

### Post by enli on 2008-06-16
I thought instead of editing the first post i would post the solution in the second post,i guess thats ok.

After thinking little bit more i thought that grub is OK ,but maybe XPs bootloader isnt.So i booted with XP installation disk and went into recovery console.

```
fixmbr
fixboot
```

Then i booted via live ubuntu disk and installed grub again as nornmally done.Inside grub :

```
find /boot/grub/stage1     #it returned (hd0,4)
root (hd0,4)      
setup (hd0)
quit
```

Voilla!! Now grub boots XP .

Thanks for not trying to help ,but hey i could keep this thread clean right ? ;D
EnLi

EDIT: edited the comment line

---

