---
title: "Fixing bootloader"
date: 2006-12-30
forum: General Help
---

### Post by Bider on 2006-12-30
The operating system is not detected, but i can still mount the xp harddrive from the live mode of ubuntu. 

I recently had to kill the process of the partition process of installation on the live side of ubuntu. but perhaps grub overwrited the current boot load, so i can access windows xp.
any suggestions?

---

### Post by bernied on 2006-12-30
Is your problem that you want to be able to boot Windows, but you can't do this easily (at the boot prompt)? Is this your problem? If not, could you please try to explain it again?

And, either way, it would be useful to see the output of the following two commands (from a linux terminal):
```
sudo fdisk -l
cat /boot/grub/menu.lst
```

---

### Post by Bider on 2006-12-30
> 
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1912    15358108+   7  HPFS/NTFS
/dev/hda2            1913       14223    98888107+   f  W95 Ext'd (LBA)
/dev/hda3   *       14224       19929    45833445   83  Linux
/dev/hda5            1913        7181    42323211    7  HPFS/NTFS
/dev/hda6            7182       14035    55054723+   7  HPFS/NTFS
/dev/hda7           14036       14223     1510078+  82  Linux swap / Solaris


The command cat /boot/grub/menu.lst brings up a command not found.
When i start the computer, it gives operating system not found.

But originally and is still there, xp should be detected.

---

### Post by bernied on 2006-12-30
Can you edit your menu.lst file? Maybe take a backup first:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
```
To try to edit the file with nano:
```
sudo nano /boot/grub/menu.lst
```
Look for the Windows entry, it should be something like this:
```
title Windows
root (hd0,0)[B]
makeactive[/B]
chainloader +1
boot
```That makeactive command is critical for you because the linux /dev/hda3 partition has the boot flag set (see the * in the output from fdisk). Linux does not need this flag to be set but Windows does. You can fix this, but maybe best to try this first.

Please post the original entry for Windows.

---

### Post by Bider on 2006-12-30
The menu.lst file does not exist, at least thats what it says.
In fact theres no grub directory in the live version of ubuntu.

---

### Post by snowx1000 on 2006-12-30
The menu.lst would not be on the boot cd, but on the ubuntu install you made from it. Ubuntu should have installed to /dev/hda# or /dev/sdb#. The best way to figure out where exactly would be to go through the installer up to the partitioning segment and go to expert or custom. That should show you some ext3 partitions. You would need to mount the root partition (try them in order if there are more than one partitions). To do this you could do something like (in a terminal window):

sudo mkdir /mnt/rootfs
sudo mount /dev/hda1 /mnt/rootfs

Then edit the menu.lst to point to the right place (/mnt/rootfs/boot/grub/menu.lst).
Now to update the bootloader do:

sudo chroot /mnt/rootfs
sudo grub-update
exit

Reboot and all should be well. It is odd that it could not find the os after the install, did you do any custom options?

You could also boot off the windows cd, get to a repair console, and do a fixmbr.
Post if you need more help.

---

### Post by bernied on 2006-12-30
Right, so you have been working only with a live-cd?

Do you want to be able to access both your ubunu install and Windows?
Or do you just want Windows back?

What you do next will depend on the answer to those two questions.

---

### Post by Bider on 2006-12-30
Just want to get windows back technically, for the time being.

---

### Post by bernied on 2006-12-30
> **snowx1000 said:**
> You could also boot off the windows cd, get to a repair console, and do a fixmbr.
Post if you need more help.
This is probably what you want to do.

Remember that your ubuntu install is still on there and, when you are feeling brave, you can get access to it fairly easily. The clues are in the rest of snowx1000's post.

Ask if you need help, there are other ways if you do not have a Windows CD.

---

### Post by Bider on 2006-12-30
I found ex3 boot drive, which was hda3. i mounted it, but i cant access any of its contents. and chroot doesnt find the directory, or filename on the mounted drive. the only ex3 drive i have is hda3.

Edit: I did not read correctly, i see hda3 has the boot flag, and i need to change this. Also i did not install ubuntu, i ran the live ubuntu, and reboot later on and it gave the error of not being able to find my original os.

---

