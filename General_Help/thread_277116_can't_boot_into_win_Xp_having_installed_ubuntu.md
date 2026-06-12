---
title: "can't boot into win Xp having installed ubuntu"
date: 2006-10-14
forum: General Help
---

### Post by tim24351 on 2006-10-14
hello

i new to ubuntu linux and searched through previous threads for a problem like mine but find one.
After i installed ubuntu from a livecd on to another partition that did not have windows on it (it had another linux on it). and last night i could boot to windows and ubuntu. But now i can only boot into ubuntu and not into windows.

here is the message i get when i try to boot into windows:
Booting 'Microsoft Windows Xp Pro'

root (hd0,0)
 filesystem type unkown, partition type 0x7
save default
makeactive
chainloader +1

Error 13: Invalid or unsupported executalbe format


any ideas?

ps im new to this

---

### Post by BoneKracker on 2006-10-14
You need to go back into ubuntu and edit the configuration file for the bootloader (it's called GRUB) and correct the settings that point to Windows.  
```

sudo gedit /boot/grub/menu.lst
```

Some possible errors are:

First, (hd0,0) might be the wrong partition.  This means "first ide drive, first partition".  Especially if your Windows was factory-installed, you might have some kind of recovery data or something in the first partition, and Windows might be somewhere else.  You should be able to use the Gnome Partition Editor (which you will have to install or use from the CD) to see a graphical picture of what partitions and filesystems are on your drives.  If you want to install it, the application's name is actually "gparted".  Alternatively, you could use the command-line tools called fdisk or parted.  You can learn about them by typing "man fdisk" or "man parted" at the command line.  You might try **(hd0,1)** if you can't figure it out.

Second, GRUB may be having difficulty accessing the partition for some reason.  You might try "rootnoverify" instead of "root".

You can also learn about grub and grub.conf by using the man pages or searching online (try [http://www.google.com/linux]("http://www.google.com/linux"))

---

### Post by tim24351 on 2006-10-14
I tried changing it to hd0,0 to hd0,1 and got a new message (error 12)
and i don't understand "rootnoverify instead of root". Could please explain more?

ps
I downloaded GParted and it says that the partition containing windows is a unknown filesystem. It also says (rightclick - infomation) "unable to detect filesystem! Possible reasons are: -The filesystem is damaged -The filesystem is unknown to libparted -There is no filesystem available (unformatted)

pss
i don't understand why its not working since i was able to boot to windows the day i installed it. I did not mess with system files only installed a few apps (texmacs,etc.)

---

### Post by BoneKracker on 2006-10-14
In gparted, you want to see if there's an NTFS partition.  

If there isn't, I suggest you boot with your Windows CD and try to repair the Windows installation, then go back and either reinstall ubuntu or manually reinstall GRUB.

What I meant was "replace 'root' with 'rootnoverify'".

---

### Post by Kateikyoushi on 2006-10-14
List your partitions please, copy the following command to terminal and give us the output.

```
sudo fdisk -l
```

---

