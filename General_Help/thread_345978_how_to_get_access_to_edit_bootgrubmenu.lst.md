---
title: "how to get access to edit /boot/grub/menu.lst"
date: 2007-01-25
forum: General Help
---

### Post by presbp on 2007-01-25
I have an external USB drive.  I have it partitioned. the first 250 gigs is backup Windows stuff (NTFS) the 2nd partition is ext3 where Ubuntu is installed and the third is the swap partition.  
 Currently I have the internal Windows drive unplugged so the only drive available is the external drive.  I have GRUB installed on the external but when I boot I get 

grub stage 1.5

grub error 17..

then I just have to shut the system down.  I think what I have to do is add 

title Windows
rootnoverify (hd1,0)
chainloader +1  

to the /boot/grub/menu.lst to allow grub to boot the external drive because it has an ntfs partition on it.  if this is correct how do I gain access to edit this??  I used the terminal and typed gksudo nautilus but when I go into boot there there is no grub file.  I think this is due to the fact that when I plug in the external drive it shows 2 devices.. external drive and usbdisk.  In gksudo nautilus I don't have access to see usbdisk.. and usbdisk is where the /boot/grub/menu.lst is located.  
Thanks.  I have been trying to get this working because I don't want to completely quit using Ubuntu I just don't want to take the chance of messing up the Windows partition like last time.

---

### Post by ajmorris on 2007-01-25
what happens when you try to "cd" to the usbdisk?

---

### Post by kvonb on 2007-01-25
If you are trying to edit the file from within X (the GUI), then open a terminal and type this:

gedit (/media/hda2)/boot/grub/menu.lst

The part in brackets should be replaced with the location that your external drive is, as I don't know if you are booting from the external to do this (although I guess not!) or from another partition or the liveCD.

or

If you are using just the terminal, type this:

sudo vi (/media/hda2)/boot/grub/menu.lst

To use vi, press the <INS> key to enter edit mode and use the arow keys to navigate.

When finished press <ESC>, then :wq<ENTER> to write and quit (including the colon).

To quit vi without saving type this:

<ESC>:q!<ENTER>

Hope that makes sense :)

---

### Post by presbp on 2007-01-25
I was trying what the previous poster said about the gedit [/media/hd0]/boot/grub/menu.lst and it just brings up a blank file.  This is odd.. usbdisk is not being found.

---

### Post by JamieC on 2007-01-25
Open a terminal window and post the output of the following:
```

sudo fdisk -l

```

---

### Post by presbp on 2007-01-25
ok I got into the file now I am going to try and edit the /boot/grub/menu.lst  
this 

title                           Windows
rootnoverify              (hd0,0)
chainloader +1    

is what I should put on it if the filesystem on the first partition of the harddrive is NTFS right??
Ubuntu is on the second partition but I think to access the drive at all it needs to have ability to boot from NTFS.. or 'chainload' if you will.  The ubuntu filesystem is ext3 and the swap is ext2.

---

### Post by presbp on 2007-01-25
I edited the file to add

title Windows
rootnoverify (hd0,0)
chainloader +1 

and I still got

grub loading stage 1.5
grub failed error 17

I am going to try editing the /boot/grub/stage1
by doing  root (hd0,0)
setup (hd1)

if that doesn't work I definitely need help.

---

