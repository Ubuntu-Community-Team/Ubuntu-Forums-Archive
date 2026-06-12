---
title: "I just reinstalled linux on a single boot system (no windows)"
date: 2006-09-05
forum: General Help
---

### Post by Roasted on 2006-09-05
And when I boot I don't get the menu that I used to prompting me to go to mem test 86 or whatever. It just goes STRAIGHT to the login screen.

Is that okay? 

Also, is there any harm in having a second drive constantly mounted? I want it to periodically throw files over on it as a backup. Would it hurt to adjust my fstab file to keep it mounted 247? And, petty question but, is there anyway to get rid of the icon on my desktop with it? :D

---

### Post by almrking on 2006-09-05
If using grub,in the /boot/grub/menu.lst file, there is a line called
hiddenmenu that is probably not commented out with "#"(# hiddenmenu). Also there is a setting before that for timeout, probably 3 seconds and a setting for "pretty colours" that is probably commented out(# color cyan/blue white/blue).

You can edit as root and change the timeout to a higher value, display the menu, which should have a regular ubuntu kernel, a recovery kernel, and a memory test, and display the menu with the standard blue color scheme.

---

### Post by Roasted on 2006-09-05
I already set it up to be mounted all the time by editing some file through fstab. Can anyone tell me what commands I'd use to make directory, mount, and unmount the devices? 

Also, what kinds of devices do you have to mount to use with linux? Just hard drives, floppy, zip, and cd roms?

---

### Post by Solver on 2006-09-06
Mount a device with

```
mount /dev/hda2 /mnt/win
```

That would mount the second partition of your first HD to /mnt/win, automatically detecting the file system. Note that /mnt/win must already exist for this to work. You can run mount without arguments to see the list of what is mounted.

Unmount with

```
unmount /dev/hda2
```

for the same device. Make directories with

```
mkdir newfolder
```.

Technically, you only need to have the device you are booting from mounted. Of course, most of the time you'll also want your floppy and CD mounted.

I personally have two hard drives, and keep both mounted at all times. Really, there's no harm to be done by having a hard drive mounted, particularly if it's a fully supported file system such as Ext3.

---

