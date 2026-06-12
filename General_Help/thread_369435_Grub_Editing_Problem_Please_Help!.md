---
title: "Grub Editing Problem Please Help!"
date: 2007-02-24
forum: General Help
---

### Post by amdalex on 2007-02-24
So right no on my computer I have Windows 98 and Ubuntu 6.10. The ubuntu drive uses ext3 and is the master drive. The windows drive is the slave and uses FAT32. I would like to know how to edit grub so when I turn on the computer it gives me a choice between windows 98 and Ubuntu. Thanks for your help.

---

### Post by Gerard Barberi on 2007-02-24
Is the second drive SATA?  You might find the information you need [here]("http://ubuntuguide.org/wiki/Dapper#How_to_boot_into_Windows_installed_on_a_seperate_SATA_drive").

---

### Post by tgalati4 on 2007-02-24
Is grub already installed?  If not:  sudo grub-install

In Ubuntu:

sudo cp /boot/grub/menu.lst /boot/grub/menu.bak

sudo nano /boot/grub/menu.lst

Title Ubuntu Edgy 6.10 Rocks!
root (hd0,1)  #This is the first drive, first partition
kernel /boot/vmlinuz_whatever_your kernel_is root=/dev/hda1 ro quiet splash
initrd /boot/initrd_whatever_your_initial_ramdisk_is
savedefault
boot


Title Windows 98 And Any Other Comments About Windows Can Go Here
root (hd1,0)                 #This is the second drive, first partition
makeactive
chainloader +1
boot

Control-0 to save and Control-X to exit

sudo more /boot/grub/device.map    (to see what your machine thinks it's devices are)




Good luck

---

### Post by amdalex on 2007-02-24
Guys just so I don't screw anything up is this what the top half of my grub file should look like?
Title Ubuntu Edgy 6.10 Rocks!
root (hd0,1) #This is the first drive, first partition
kernel /boot/vmlinuz_whatever_your kernel_is root=/dev/hda1 ro quiet splash
initrd /boot/initrd_whatever_your_initial_ramdisk_is
savedefault
boot


Title Windows 98 And Any Other Comments About Windows Can Go Here
root (hd1,0) #This is the second drive, first partition
makeactive
chainloader +1
boot
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0
I just noticed how do I figure out what my kernal is?
If I save my grub file like this will it then give me a choice between windows 98 and Ubuntu 6.10? 
Thanks for your help.:)
Also I am pretty new to Linux so could you keep it easy to follow. I could not follow your first instructions.

---

### Post by tgalati4 on 2007-02-24
Here's what my /boot looks like:

abi-2.6.15-26-386     grub                      System.map-2.6.15-26-386
abi-2.6.15-28-386     initrd.img-2.6.15-26-386  System.map-2.6.15-28-386
config-2.6.15-26-386  initrd.img-2.6.15-28-386  vmlinuz-2.6.15-26-386
config-2.6.15-28-386  memtest86+.bin            vmlinuz-2.6.15-28-386


the files vmlinuz-2.6.15-28-386 and initrd.img-2.6.15-28-386 are what go into menu.lst.

Your kernel will be different (probably higher version) since you are running Edgy and I am running Dapper.

Back up your existing grub menu.lst first.

Put your edits at the very end, not at the top since updates to Ubuntu will automatically modify menu.lst to reflect the latest kernel as it gets updated.  In time, you will have several kernels to boot from.  Typically you will boot with the latest unless something breaks.  Then you can go back to a previous kernel that will (presumable) still work.

Look in your /boot and pick out your kernel and initrd (inital ramdisk image)

grub can also find your kernels by hitting escape or "c"  while grub menu is showing and typing in ```
kernel /boot/vmlinuz (tab key)
```

This is the interactive mode of grub.  Hit "b" to boot.  Of course give it a root  (hd0,0) and initrd /boot/initrd_whatever beforehand.

Don't forget to check your /boot/grub/device.map to see what your (hd0,0) code is.

Type help at the command line to get a list of commands.  Grub is worth getting to know.

Good luck.  We're cheering for you.

---

### Post by amdalex on 2007-02-24
What is a ramdisk?

---

### Post by amdalex on 2007-02-24
Also can I edit the grub file with the text editor? In terminal when I type (control key) O it doesn't save and when I type (control key) X it does not exit. Any ideas?

---

### Post by Maestro23 on 2007-02-24
> **amdalex said:**
> Also can I edit the grub file with the text editor? In terminal when I type (control key) O it doesn't save and when I type (control key) X it does not exit. Any ideas?

> sudo nano -B /boot/grub/menu.lst


-B makes a backup of the file before you edit it.

---

### Post by tgalati4 on 2007-02-24
A ramdisk is a temporary disk drive that is created in memory only.  Grub needs the proper kernel and initrd  to boot into a "mini" kernel so that Linux can run its hardware detection without touching any disk.  When all the of hardware is detected, the operating system can load normally from the harddisk freeing up the ramdisk since it is not needed anymore.

Good luck.

---

### Post by amdalex on 2007-02-25
I am still confused about what to specify for the ramdisk. Also again can I just edit the grub file with the text editor?

---

### Post by Maestro23 on 2007-02-25
> **amdalex said:**
> I am still confused about what to specify for the ramdisk. Also again can I just edit the grub file with the text editor?

> sudo nano -B /boot/grub/menu.lst

nano is a text editor

---

### Post by amdalex on 2007-02-25
So I entered the windows entry one space after the line that said #end debian kernel and a few other things. So now when I hit the windows entry in the grub menu on boot it just hangs with a line of goofy looking code. Also I have to mount the windows drive manually every time I boot windows. Is there any way to keep the windows drive mounted after a reboot? What do you guys think might be my problem?:confused:

---

### Post by amdalex on 2007-02-25
bump.

---

### Post by tgalati4 on 2007-02-25
Remember, anything after a # is a comment on the same line.  I assume that you put the windows grub commands at the very end of the file on a new line.

It should look like:

Title Windows XP
root (hd0,0)
chainloader +1 
makeactive
savedefault
boot


This assumes that windows is on the first disk, first partition.  Your /boot/grub/device.map will have a list of root codes that you can try.

Remember, hd0 is the first disk, hd1 is the second disk, hd2 is the third disk
hd0,0 is the first partition, hd0,1 is the second partition, hd0,2 is the third partition.

Hey I didn't write grub, and yes it is confusing.

---

### Post by amdalex on 2007-02-26
Do you guys thinks I should get rid of the line that says ##end debian atoumagic kernel bla bla bla"? Then should I place the windows entry one space after the last ubuntu entry?

---

### Post by tgalati4 on 2007-02-26
You don't need to delete the ##end debian line.  It is there for a reason.  You should add your stuff on a new line after the automagic line.  The stuff in the automagic section gets changed whenever you perform an update and the kernel gets bumped up a version.

The grub menu items at the bottom will always remain.  That is why you put the windows stuff at the bottom.

Good luck.  Spend some time learning grub as it will pay dividends in the future--especially helping others convert from Windows!

The ramdisk is not something you need to worry about.  The initrd line stands for initialize ramdisk.  It is part of the Linux bootup sequence.  You need the root line, kernel line and initrd line to boot properly.

---

### Post by amdalex on 2007-02-28
Do I put the windows entry one space or two or whatever spaces after the automagic line? Do you have any ideas about why it came up with all the funny looking code. I wasn't even letters it looked like Chinese.:lolflag:

---

### Post by tgalati4 on 2007-03-01
Perhaps you are running a Chinese version of Ubuntu.  Then of course the code would look like Chinese.

---

### Post by amdalex on 2007-03-10
Bumpity bump

---

### Post by confused57 on 2007-03-10
Maybe an entry similar to this will boot your Windows drive:

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1

Place it at the very end of your menu.lst file.

---

### Post by amdalex on 2007-03-24
Thanks, confused I entered what you said and it booted windows. Thanks alot.:biggrin:

---

### Post by amonroe on 2007-04-08
I cant seem to get into my grub list to edit it 7.04 works diffrence from 6.10 how do i get into grub to edit.

---

### Post by tgalati4 on 2007-04-08
I think menu.lst is now grub.conf.

sudo nano -B  /boot/grub/grub.conf

---

### Post by Maestro23 on 2007-04-08
> **amonroe said:**
> I cant seem to get into my grub list to edit it 7.04 works diffrence from 6.10 how do i get into grub to edit.

It is the same on Edgy and Feisty.

> /boot/grub/menu.lst

---

