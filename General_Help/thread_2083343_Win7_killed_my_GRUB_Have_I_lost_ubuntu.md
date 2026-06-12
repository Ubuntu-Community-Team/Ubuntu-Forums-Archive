---
title: "Win7 killed my GRUB: Have I lost ubuntu?"
date: 2012-11-12
forum: General Help
---

### Post by DaveBF on 2012-11-12
I started my computer and walked away.  Windows began it's diagnostics and when I returned I restarted at chose GRUB from my boot menu (I installed through WUBI)

Instead of loading GRUB as usual and showing me a list of my Ubuntus, it loads GRUB1.99ubuntu2.3 or something ridiculous like that (I have Ubuntu 12.04).

There is nothing available but a <grub> terminal and the option to press TAB for a list of commands.  What the heck happened and how the heck do I get back into ubuntu?

Thanks,

Perplexed Dave

---

### Post by cottfcfan on 2012-11-12
Try booting into a live cd/usb of Ubuntu 12.04.
Open a terminal & paste the following commands:
```
sudo mount /dev/sdXY /mnt
```
```
sudo grub-install --boot-directory=/mnt/boot /dev/sdX
```
```
sudo update-grub
```
X = the hard drive id (usually "a" unless 2 hard drives are installed)
Y = The partition Ubuntu is installed on.

ps if you are unsure paste a copy of your partition table.

---

### Post by raja.genupula on 2012-11-12
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by DaveBF on 2012-11-12
Thanks to the both of you.

I  have to leave for class now, but I'll give these a try in a couple of hours.  It seems straight-forward.  Thanks a lot!

---

### Post by Cavsfan on 2012-11-12
**cottfcfan**'s or **raja.genupula**'s method should get you back to normal.
Once you get the grub menu normal and able to boot into Ubuntu and Windows, you might be interested in sprucing up your Grub2 menu
with the Community Wiki in my signature. It is pretty straightforward.
If you do not like it there are instructions at the bottom for restoring it back to default.

It never has to be edited. I got tired of changing the default line every time a kernel got installed as I have the default Windows for my wife.

This method was taught to me by a member of this forum **Ranch Hand** and it works well on any Ubuntu. I have even had Debian Squeeze in the mix and that also worked.

---

### Post by DaveBF on 2012-11-12
So here's the story so far:

I booted into Ubuntu Secure Remix and used [Boot-Repair]("http://paste.ubuntu.com/1353580").

Now startup loads GRUB2 with the options for ubuntustudio and the win7 launcher.  However, the Ubuntu 12.04 I've been using still won't boot.

ubuntustudio is a separate deal altogether.  It boots fine, but to open up my Ubuntu12.04 I have to go through the win7 launcher (installe with wubi).  GRUB takes me there fine, but my win7 launcher is unable to open Ubuntu.  This is when it crashes and takes me to a grub> command line.

How do I get back into my Ubuntu 12.04?

---

### Post by raja.genupula on 2012-11-12
you need to add a boot entry then . 
follow this [http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/](http://www.linuxbsdos.com/2012/03/10/restore-the-windows-bootloader-to-mbr-after-dual-booting-with-linux/)

---

### Post by bcbc on 2012-11-12
Your root.disk is missing or corrupted. You need to run chkdsk and then hopefully it repairs it. See here for info: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

PS I don't advise using boot-repair with wubi installs. Not sure whether forcing fsck on a root.disk with ntfs corruption will cause damage:
```
mount -o loop /mnt/boot-sav/sda3/ubuntu/disks/root.disk /mnt/boot-sav/wubi1
mount: /dev/loop1: can't read superblock
The file browser that just opened will let you access your Wubi (Linux installed into Windows) files. (/mnt/boot-sav/wubi1/home) Please backup your data now! Then close this window.
xdg-open: file '/mnt/boot-sav/wubi1/home' does not exist
umount /mnt/boot-sav/wubi1
umount: /mnt/boot-sav/wubi1: not mounted
This will try to repair Wubi filesystem. Please backup your data before this operation. Do you want to continue? yes
fsck -f -y /mnt/boot-sav/sda3/ubuntu/disks/root.disk
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /mnt/boot-sav/sda3/ubuntu/disks/root.disk
Could this be a zero-length partition?
```

---

