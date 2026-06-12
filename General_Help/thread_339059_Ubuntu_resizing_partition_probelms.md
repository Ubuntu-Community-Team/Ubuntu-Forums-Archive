---
title: "Ubuntu resizing partition probelms"
date: 2007-01-15
forum: General Help
---

### Post by m0u53m4t on 2007-01-15
Im trying to resize my Ubuntu partition, but it wont go any bigger even though I've got 13gb of unallocated space ](*,)  Help!
[IMG]http://i5.photobucket.com/albums/y198/Miniclipunblocked/error1.png[/IMG]

---

### Post by bodhi.zazen on 2007-01-15
You have to move the ubuntu partition so you go from

hda1
free space
ubuntu root partition

to

hda1
ubuntu root partition
free sapce

Make a new partition, copy (move) ubutnu, then resize

Note: After the move you will need to update /boot/grub/menu.lst and /etc/fstab

See here for info:

[http://www.ubuntuforums.org/showthread.php?&t=316237](http://www.ubuntuforums.org/showthread.php?&t=316237)

---

### Post by m0u53m4t on 2007-01-15
Great, I get all that, but what do you mean "update /boot/grub/menu.lst and /etc/fstab"?

Do I do that from the LiveCD disk or through my installation?

---

### Post by bodhi.zazen on 2007-01-15
from the live CD or Ubuntu will not boot ...

---

### Post by m0u53m4t on 2007-01-15
I forgot... Now I can't boot. Is there any way to fix that?

---

### Post by Irony on 2007-01-15
To copy Ubuntu first format the unallocated partition as ext3 - then via a live CD copy it over;

[http://www.pclinuxos.com/forum/index.php?topic=13404.0](http://www.pclinuxos.com/forum/index.php?topic=13404.0)

If you look at your menu.lst and fstab files you will see they refer to your / partition and other partitions and they might need editing.

As it happens in your case they may not need editing because if you format your unallocated partition it will become hda2 - note when you format that partition that your present Ubuntu partition may become hda3; use  the live CD to determine your parition table by doing, in terminal;

[PHP]sudo fdisk -l[/PHP]

---

### Post by Irony on 2007-01-15
You have to install grub and point it at the new partition.

Ubuntu is now probably in hda3 rather than hda2 so point grub at hda3.

---

### Post by m0u53m4t on 2007-01-15
How? Thats all I get when I turn my pc on and I cant boot from LiveCD

---

### Post by Irony on 2007-01-15
To install grub (I use a Hoary disc), don't know how it works with newer ones, do;

[PHP]Boot from the install ubuntu CD and at the prompt typed;
boot: rescue
Go to a  mount points, hda5 would be;
dev/disc/disc0/part5
At the sh-3.00# prompt type;
grub-install /dev/hda
After being returned to the prompt, do;
#umount /dev/hda5
#reboot  [/PHP]

---

### Post by m0u53m4t on 2007-01-15
> **m0u53m4t said:**
> I cant boot from LiveCD
So I cant get to any way to enter data...

---

### Post by bodhi.zazen on 2007-01-15
LOL Why not ? do you not have a CD or will it not boot ?

At any rate, you can access the files form windows (if you can boot to windows):

[http://www.fs-driver.org/](http://www.fs-driver.org/)

If that fails you will need to make a boot floppy ?

---

### Post by m0u53m4t on 2007-01-15
*Phew* A few quick hard reboots fixed that. I've now booted onto LiveCD.

How do I update those things so it works now?

---

### Post by bodhi.zazen on 2007-01-15
Mount your Ubuntu root partition (hda2 ?)

```
sudo mkdir /media/ubuntu
sudo mount /dev/hda2 /media/ubuntu
```

Now fstab:```
gksudo gedit /media/ubuntu/etc/fstab
```

Change your root partition:

/dev/hda2 / .......

Save and exit.

Now grub:```
gksudo /media/ubuntu/boot/grub/menu.lst
```

Look at your ubuntu stanzas.

Change to:

root (hd0,1)

kernel /boot/vmlinuz..... root=**/dev/hda2** ....

Save and exit.

Should be good to go. Of course if Ubunt is not hda2 you will need to modify somewhat.
..

HTH 8)

---

### Post by m0u53m4t on 2007-01-15
Ok, done all that, but I'm still getting error 22.

I've just noticed there's still a startup option for windows in the menu.lst even though I've delete its partition. Do I need to remove that as well then?

---

### Post by bodhi.zazen on 2007-01-15
Lets re-install grub.

What is your Ubuntu partition ?

If you do not know, post the output of :```
sudo fdisk -l
```

---

