---
title: "Cannot Mount Volume"
date: 2007-04-09
forum: General Help
---

### Post by joep on 2007-04-09
Hi I have a Maxtor 3200 External Hdd When I plug it in by usb I get this Message.
Cannot mount volume.
Invalid mount option when attempting to mount the volume. 

Any help appreciated.

---

### Post by joep on 2007-04-09
managed to find this is it any help ?

Disk /dev/sda: 163.9 GB, 163927522816 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19552   157051408+  83  Linux
/dev/sda2           19553       19929     3028252+   5  Extended
/dev/sda5           19553       19929     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

---

### Post by eggdeng on 2007-04-09
I don't know how familiar you are with manually mounting disks. The usual procedure is to create a directory to mount it to by typing in a terminal, for example ```
sudo mkdir /media/externaldisk
``` Next mount the partition in that directory. Assuming the disk has only one partition & this is called sdb1, type ```
sudo mount /dev/sdb1 /media/externaldisk
```

---

### Post by joep on 2007-04-09
Hi I'm a newbie to Linux.
I followed your insructions heres a print out.

joe@joe-desktop:~$ sudo mkdir /media/externaldisk
joe@joe-desktop:~$ udo mount /dev/sdb1 /media/externaldisk
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo
Make sure you have the 'universe' component enabled
bash: udo: command not found
joe@joe-desktop:~$ sudo apt-get install udo
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  udo
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 177kB of archives.
After unpacking 532kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe udo 6.4.1-1 [177kB]
Fetched 177kB in 1s (115kB/s)                      
Selecting previously deselected package udo.
(Reading database ... 152066 files and directories currently installed.)
Unpacking udo (from .../archives/udo_6.4.1-1_i386.deb) ...
Setting up udo (6.4.1-1) ...
joe@joe-desktop:~$

---

### Post by joep on 2007-04-09
eggdeng   Thank you it worked can't tell you how grateful I'am could of lost all that data. Once again thanks Joep :guitar:

Will I have to give that command all the time or is there a way to automate it.

---

### Post by eggdeng on 2007-04-10
> **joep said:**
> Hi I'm a newbie to Linux.
I followed your insructions heres a print out.

joe@joe-desktop:~$ sudo mkdir /media/externaldisk
joe@joe-desktop:~$ udo mount /dev/sdb1 /media/externaldisk
The program 'udo' is currently not installed.  You can install it by typing:
sudo apt-get install udo


If you check my post, you'll see that 'udo' is a typo for 'sudo', the command which allows you to act as superuser. The shell understood that you wanted to run the command 'udo' (apparently there is a programme which goes by this name) and helped you to install it from the repositories. Whatever it is that you installed, I'm sure it has nothing to do with mounting the disk. If you want to get rid of it the same way as you installed it, type
```
sudo apt-get remove udo
```
apt-get is the command which retrieves the files you want from the repositories on the internet, apt-get install whatever retrieves and installs whatever, apt-get remove whatever removes it.
In this case, because you had already run sudo correctly in the previous line, the shell went ahead, ran the mount command and you got your disk. You may find after this that ubuntu mounts the disk automatically but if it doesn't, you can create a little script to speed things up. Create a file mountdisk.sh (the name doesn't matter) by typing

```
sudo gedit mountdisk.sh
```

Copy and paste the following to the new file and save it to your /home/joep directory (assuming joep is your username).

```

#!/bin/bash
sudo mount -v /dev/sdb1 /media/externaldisk

```

Make it executable by running

```
chmod +x mountdisk.sh
```

Now when you need to mount the disk, just run mountdisk.sh from a terminal. If you want to have the disk available on startup, remove the sudo and the following space from the file mountdisk.sh, copy  it to the /etc/init.d directory and make it executable as before. The commands for these last two steps are

```
sudo cp mountdisk.sh /etc/init.d
```

and

```
sudo chmod +x /etc/init.d/mountdisk.sh
``` 

NB: Remember to always unmount the disk before unplugging it 

```
sudo umount -v /dev/sdb1
```

& watch the typos!

---

### Post by joep on 2007-04-10
Once again thanks. It is now working fine. Don't know if I'll ever get the hang of Ubuntu but apart from the odd panic it's put the fun back in computers for me. :grin:

---

### Post by Van_Man on 2007-11-25
> **joep said:**
> Hi I'm a newbie to Linux.
I followed your insructions heres a print out.

joe@joe-desktop:~$ sudo mkdir /media/externaldisk
joe@joe-desktop:~$ udo mount /dev/sdb1 /media/externaldisk




Hi I'm getting the same problem but it's not working for me this is what it'scoming up with...


jim@ho0ks:~$ sudo mount /dev/sdb1 /media/externaldisk
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/externaldisk -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/externaldisk ntfs-3g defaults,force 0 0


Any help would get much appreciated.

---

### Post by rollersnaeks on 2007-11-28
I'm having the exact same problem and error message as Van_Man here and would like some help, if possible.

Just installed Ubuntu today after Vista bugging on me and refusing to start for the nth time, so I'm clueless.
I don't have any version of Windows installed, so choice #1 is irrelevant.

Trying choice #2 I get this;
"mount: only root can do that"

I'm guessing it's awfully simple, but how do I proceed from here?
Many thanks in advance for any help.

---

### Post by eggdeng on 2007-11-28
You need to prefix ```
sudo
``` to the command. sudo is the command which allows you to act as superuser, in effect, root.

---

### Post by hbohn123 on 2007-11-28
> **eggdeng said:**
> I don't know how familiar you are with manually mounting disks. The usual procedure is to create a directory to mount it to by typing in a terminal, for example ```
sudo mkdir /media/externaldisk
``` Next mount the partition in that directory. Assuming the disk has only one partition & this is called sdb1, type ```
sudo mount /dev/sdb1 /media/externaldisk
```

nice job eggdeng :)

---

### Post by shanerdaner on 2007-11-28
> **eggdeng said:**
> I don't know how familiar you are with manually mounting disks. The usual procedure is to create a directory to mount it to by typing in a terminal, for example ```
sudo mkdir /media/externaldisk
``` Next mount the partition in that directory. Assuming the disk has only one partition & this is called sdb1, type ```
sudo mount /dev/sdb1 /media/externaldisk
```

Thanks this worked wonderfully!!!!

---

### Post by xerxesdaphat on 2007-12-19
I was having the identical problem with a USB flash drive. Even manually mounting it didn't work. Was very confused, until I fired up gparted, which clued me onto the fact I'd edited my /etc/fstab a while back to add an entry for /dev/sdb1 to mount at /mnt/backup (this was for an external hard-drive for backups). The memory key also went by /dev/sdb1, so it was trying to mount a FAT32 flash drive as an ext3 external HDD, which didn't work of course. I commented out this line in /etc/fstab and the flash drive worked as normal afterwards.

Just an additional thought in case you're scratching your head.

---

### Post by vladicabg on 2007-12-19
I had a same problem like Van_Man and rollersnaeks and the error message gives the same command as eggdeng post. So I  tried 

sudo mount command from the error message. In my case it was sdb5. I created mountdisk.sh script to be copied into /usr/local/bin/ 
Then you can do 

sudo mountdisk.sh start and to mount
sudo mountdisk.sh stop to unmount

#!/bin/bash
endscript () {
date +"------------ "%F" "%X" "%Z" End MountDisk Script"
exit $1
}
case "$1" in
'start')
    echo "Mounting disk"
    sudo mount -t ntfs-3g /dev/sdb5 /media/externaldisk -o force
    endscript 0
    ;;

'stop')
    echo "Unmounting disk"
    sudo umount -v /dev/sdb5
    endscript 0
    ;;
*)
    echo "Usage: $0 { start | stop }"
    ;;
esac
exit 0

---

### Post by centurian on 2008-01-16
I also had the same problem, i got two solutions to it
1) [https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")
2) I updated my **gnome-mount** and **gnome-volume-manager** packages to 0.7-2 and 2.22.0-1 respectively (the latest ones) using **sid** reprository of **debian**. Before updating these packages, I had also purged the old packages.

I prefer the second one, its more easier and safe (i think).

centurian

---

### Post by Endolith on 2008-04-27
I get the same error message and my USB drives won't mount automatically.

They mount fine by hand, but I am sick of doing it by hand and I'm not going to put them permanently in my fstab when they're removable drives.

I've had this problem for a year now. Anyone figure out the auto-mounting problem?

[http://ubuntuforums.org/showthread.php?t=608210](http://ubuntuforums.org/showthread.php?t=608210)

---

