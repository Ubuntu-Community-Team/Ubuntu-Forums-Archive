---
title: "Have a slight problem"
date: 2008-04-26
forum: General Help
---

### Post by masterskop on 2008-04-26
Hi,

Complete noob here....I have ubuntu 7.10 install on another hhd when 7.10 first came out.  So, this morning I thought that I could remove that drive an place it into another computer.  End result was that it would not boot up.  I think it was looking for another drive which is still in the other machine.  Can this be easily fixed?

Would I 
a: reinstall 7.10
b: insert the 7.10 and boot up w/ the cd and what could I do here to fix the problem

Also, any and all suggestions welcomed

---

### Post by ryanhaigh on 2008-04-26
You will most likely need to reinstall grub, [this link]("https://help.ubuntu.com/community/GrubHowto#head-f60bd54bfea5b5afbbb8eab20586240d973cdde3") should have everything you need.

---

### Post by masterskop on 2008-04-26
ryanhaigh,

Here some additional information:

Booting 'Ubuntu, Kernel 2.6.15-28-386'

Root (hd0,6)
File System type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz-2.6.15-28-386 root=/dev/hde7 ro quiet splash
[Linux-bzImage, setup=0xlc00, size=0x157a58]
initrd /boot/initrd.img-2.6.15-28-386
[Linux-initrd @ 0x1f979000, 0x676774 bytes]

Safedefault
boot
uncompressing Linux...ok, booting the kernel
[17179570m 392000] PCI: Cannot allocate resource regions of cluster 0000:00:00,0
Alert: /dev/hde7 does not exist. Dropping to shell!

goes on from there about not accessing tty

This hdd drive came from my other machine and I could remember how the setup was.  Looks like from this information that the kernel was one another drive?

---

### Post by ryanhaigh on 2008-04-26
No the kernel is still on this drive, the problem is that the drive isn't in the same place any more, before your system was on /dev/hde7 now it might be on /dev/hda7 or hdb etc. You can boot your system without the livecd if you can work out where the / partition is. When the system drops to the shell use the following:
```

ls /dev/ | grep hd
ls /dev/ | grep sd

```
That should show you all the available partitions, from there you should be able to identify what used to be /dev/hde7 (unless you have a few disks with that many partitions), then you can reboot the computer, press ESC when grub comes up, press E to edit the first entry, go to the second line that begins with kernel, press E again, change root=/dev/hde7 to root=/dev/whateveritis, press ESC, then press B to boot that kernel. 

With any luck that will boot your system and you will then need to reinstall grub using the howto I linked to in my last post.

---

### Post by masterskop on 2008-04-26
hi ryanhaigh,

Found the /dev/ partition finally!  Then I booted over and got a few more errors.  Apparently, the filesystem couldn't be loaded correctly.  The boot drive was hde7 and is now hdd7, so all the other /dev/ partitions that are being looked for start w/ hde and the system just hung.  

I went into the live cd but when I got to the terminal and tried to log on as superuser... i could not remember my password.  I did open up the root but there was not grub.  So, if I'm not logged in as a superuser, I won't see the grub, right?

So, now i'm on the search in order to reset the root password

---

### Post by masterskop on 2008-04-26
Well I'm one step further but I'm stuck.

I don't have a "/" or "/boot" ... but I do have the following after putting this drive back into the original machine:

/dev/sda
  /dev/sda1  ntfs    /media/sda1  (this is my bootable winxp)
  /dev/sda12                       0 mb    unknown
  /dev/sda5  ext3    /media/sda5   2500 mb
  /dev/sda11                       0 mb    unknown
  /dev/sda6  swap                  2146 mb
  /dev/sda10                       0 mb    unknown
  /dev/sda7  ext3    /media/sda7   2600 mb
  /dev/sda9  ext3    /media/sda9    792 mb
  /dev/sda8  ext3    /media/sda8   2400 mb

so, do i need to do a reinstall of this OS?  Or, is this easy to fix?

---

### Post by masterskop on 2008-04-26
Need some more help...

After searching the forums for the passed 3 hrs, I figured out that I had to use the following:

blkid

and 

cat /etc/fstab

in order to find out if my partitions were the same...they were not.  After copying the information from the blkid "uuid's" to the fstab file via gedit, i got to boot up finally to the password screen.  I got stuck there.  I need to be able to create a user and a password or a way to deactivate the login screen and just get to the desktop...any help is appreciated....

---

### Post by ryanhaigh on 2008-04-26
If you have lost your password you can follow this guide to reset it:
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

---

### Post by ebelog on 2008-04-27
You'll probably save yourself some time and hassle by reinstalling when you move a hard drive to a different computer. With a little effort, it's possible to move the boot drive to new hardware, but it's almost always more straight-forward and easier to install Ubuntu again.

---

### Post by masterskop on 2008-04-27
Thank you both,

Yes, I thought about that as a last resort.  I'll reinstall the OS.  BTW, is it possible to keep the windows partition but just redo the ubuntu part?

---

