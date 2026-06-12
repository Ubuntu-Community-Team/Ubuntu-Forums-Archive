---
title: "Menu.lst change"
date: 2007-11-14
forum: General Help
---

### Post by AllanP on 2007-11-14
Solved: Ubuntu on MBR. Had Fedora 8 loaded and on menu.lst. I couldn't get java working in Fedora 8 so re installed Fedora 7 over it. Now of course my menu.lst isn't correct. I also had to change partition ID's in Ubuntu's Fstab. I can't access the partition that F7 is on to check its' grub.conf. I need the ID for F7 to put in my Ubuntu menu.lst. Any ideas.
I can boot to Ubuntu ok. TIA.

---

### Post by mahiyar on 2007-11-14
run in cli >sudo blkid or >sudo [COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh to find your UUID's
[/FONT][/COLOR]

---

### Post by AllanP on 2007-11-14
I've done blkid but, figured I had to change version #'s. Edit: don't see any partition addy in menu.lst. Here's the id for the partition and the menu entry for Fedora:

/dev/sda3: LABEL="/12" UUID="2d9d00d3-4809-4f57-b65d-97f70d497dbd" SEC_TYPE="ext2" TYPE="ext3" 


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda3.
title		Fedora (2.6.23.1-49.fc8) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.23.1-49.fc8 ro root=LABEL=/12 rhgb quiet 
initrd		/boot/initrd-2.6.23.1-49.fc8.img
savedefault
boot

---

### Post by mahiyar on 2007-11-14
If you can access Ubuntu, can you mount fc7 partition manually or chroot in to it as described here roughly
1) Open a Terminal (Applications->Accessories->Terminal)
2) Run "sudo -s"
3) Run "mkdir /ubuntu"
4) Run "mount /dev/sdc1 /ubuntu" (where /dev/sdc1 is your Fedora Linux root partition)
6) Run "chroot /ubuntu"
7) Run "cd /boot/grub"


Change menu.lst etc... I do not think on changing from fc8 to fc7 changes the UUID changes, it is partition specific not system specific. Correct me if Im wrong.

---

### Post by AllanP on 2007-11-14
Solved: Thanks. Actually I used SuperGrub CD; got into Fedora7 and copied the Menu.lst entries to a USB stick, booted back to Ubuntu and pasted them into the Ubuntu Menu.lst.

---

### Post by mahiyar on 2007-11-15
Glad your problems solved, always more than one ways to do things in Linux :)

---

