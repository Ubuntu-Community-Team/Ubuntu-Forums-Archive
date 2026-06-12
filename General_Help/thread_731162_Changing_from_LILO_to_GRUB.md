---
title: "Changing from LILO to GRUB"
date: 2008-03-21
forum: General Help
---

### Post by mgoldsby on 2008-03-21
I somehow managed to install LILO during Ubuntu 7.10 installation. Can I change to GRUB without reinstalling Ubuntu?  I did
  apt-get install grub
so grub is there.  However, the ONLY thing in my /boot/grub directory is a device.map file (created, I think, when I did "sudo grub"), which shows  hd0 to be /dev/sda.  (I have two partitions on /dev/sda, a boot partition followed by a logical volume partition.)
Thanks for any help--
--Mike

---

### Post by bodhi.zazen on 2008-03-21
yea, it is easy. You need to know your partitions names.

Use your /boot partition as root.

```
sudo grub

grub > root (hd0,x)
grub > setup (hd0)
grub > quit
```

where hd0,x is your boot partition, my guess is (hd0,0)

---

### Post by mgoldsby on 2008-03-21
Thanks, bodhi.zazen, but when you say "use your /boot partition as root", what does that mean exactly?
Thanks,
--MIke

---

### Post by mgoldsby on 2008-03-21
Never mind, I understand now.
Thanks again,
--Mike

---

### Post by mgoldsby on 2008-03-21
HOWEVER, the command sequence
  grub
  grub> root (hd0,0)
  grub> setup (hd0)
FAILS saying it can't find stage1 in /boot/grub.  This even though after it failed the first time I copied /usr/lib/grub/i386-pc/stage1 to /boot/grub, so /boot/grub/stage1 is verifiably there.
Any ideas?
Thanks,
--Mike

---

### Post by Irony on 2008-03-21
Here are my notes;

To redirect/install grub to the MBR (hda) and point it to a menu.lst in hda3 do;

```
sudo grub
```

This opens up the grub program, with a prompt of grub>, now type. 

```
find /boot/grub/stage1
root (hd0,2)
setup (hd0)
quit
```

Here is the output;

```
grub> find /boot/grub/stage1
 (hd0,2)
 (hd0,5)
 (hd0,6)
 (hd0,8)
 (hd0,11)
 (hd1,1)
 (hd1,2)

grub> root (hd0,2)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  15 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+15 p (hd0,2)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded

grub> quit
```

---

### Post by bodhi.zazen on 2008-03-21
Try :

```
sudo grub-install /dev/sdxx
```

where /dev/sdxy is your boot partition.

Then you may need to repeat the steps in my first post (not sure about that).

---

### Post by mgoldsby on 2008-03-21
Thanks again, Bodhi and Irony.
However,
grub> find /boot/grub/stage1
gives 'File does not exist'.
And when I try  # grub-install /dev/sda, the error is
'/dev/mapper/system-root does not have any corresponding BIOS drive'.
My next tactic is to reinstall 7.10 server, this time without LVM.  When I installed it without LVM before, it gave me GRUB automatically.  (I don't recall it asking when I did the LVM install, it just gave me LILO.)
--Mike

---

### Post by bodhi.zazen on 2008-03-21
mount your boot partition at say /mnt

then :

```
sudo grub-install --root-directory=/mnt /dev/sda
```

At least that worked for me ;)

---

### Post by mgoldsby on 2008-03-22
Maybe some progress:
I tried the following:
mount /dev/sda1 /mnt
grub-install --root-directory=/mnt /dev/sda
It displayed
  "(hd0) /dev/sad
Installation finished.  No error reported."

Then I ran update-grub.  Afterwards, I didn't see any parameters in menu.lst I wanted to change.

Then I tried rebooting, and it took me to the grub prompt.  I took the opportunity to do the following:
  grub> find /boot/grub/stage1
It found it as (hd0,0), so then I did
  grub> root (hd0,0)
  grub> setup (hd0)
Grub then reports embedding efs2_stage1_5 and installing stage1 and says "..succeeded. Done."

I was encouraged by this and tried rebooting.  However, it just takes me right back to the grub prompt.

Can you think of anything reasonable to try next?

Thanks,
--Mike

---

### Post by bigredradio on 2008-03-24
If you have your root filesystem on LVM, you MUST have a /boot filesystem built on a partition. Inside that /boot partition needs to be an initrd that starts up LVM. Otherwise the kernel cannot get access to the real root filesystem and you get a kernel panic.

---

