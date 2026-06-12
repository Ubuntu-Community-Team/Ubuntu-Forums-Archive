---
title: "/etc/fstab"
date: 2012-12-20
forum: General Help
---

### Post by MikeCyber on 2012-12-20
Hi
in 10.04 I mount a ntfs partition and can execute a *.sh there. But on 12.04 I cannot execute that shellscript. I don't understand the fstab. What do I need to change to get back 10.04 functionality?
Thanks

---

### Post by sahabcse on 2012-12-20
Please provide more info.

Do you want to mount ntfs partition permanently?

The /etc/fstab file contains static filesystem information. It defines how storage devices and partitions are to be mounted and integrated into the overall system. It is read by the mount command to determine which options to use when mounting a specific device or partition.

---

### Post by sudodus on 2012-12-20
You need execute permission to run a file, and for the Windows file systems FAT and NTFS the file permissions are set when the partitions are mounted (they cannot be set individually).

One solution is to collect your own executable binary files (compiled programs) and shell-scipt files in your own bin directory

```

mkdir ~/bin
cd ~/bin
mv 'files-to-execute' .
```

and set the executable bits

```
chmod ugo+x 'files-to-execute'
```

Another method is to give all files in the FAT or NTFS partition execute permission (in /etc/fstab)

A third method works for shell scripts: run them as a parameter to sh, bash, csh etc:
```
bash 'file-to-execute' parameter1 parameter2 ...
```
```
sh script.sh
```

---

### Post by LiamOS on 2012-12-20
Is there an entry in /etc/fstab for your NTFS partition?
If so, you could post the fstab and we can have a look at how it's being mounted.

---

### Post by MikeCyber on 2012-12-20
Well I'm fine by clicking on the drive to open/mount it, but I wonder why I cannot execute on 12.04/Win-F anymore.

10.04 fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=009e61ed-f63d-4221-868c-f42c6590b726 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda7 during installation
UUID=2d1c22fb-e985-4d6f-b134-4b3224931d09 /home           ext4    defaults        0       2
#UUID=57b9d08d-5942-4142-b06a-683155ad6df4 /media/DATA     ext4    defaults        0       0
#UUID=58E0EFA0E0EF831C /media/Win-F                        ntfs    defaults        0       0
# swap was on /dev/sda5 during installation
UUID=ec76bdbf-883b-49e1-92be-9c817bbc40c3 none            swap    sw              0       0
/dev/sr0        /cdrom  auto    rw,user,noauto,exec,utf8 0       0


12.04 fstab:

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb8 during installation
UUID=e40f7fad-71dc-4ead-80d0-d13d4d0a0af5 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=ec76bdbf-883b-49e1-92be-9c817bbc40c3 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

Thanks

PS: Well it works alike bash script.sh thanks, but not anymore alike ./script.sh

---

### Post by sudodus on 2012-12-20
So there is no entry for your NTFS drive in [FONT="Courier New"]/etc/fstab[/FONT]. When mounted there is probably an entry for it in [FONT="Courier New"]/etc/mtab[/FONT], and that should show that it is mounted without execute privileges. That can be changed temporarily with ***umount*** and ***mount*** (with the correct options, and changed persistently with an entry in [FONT="Courier New"]/etc/fstab[/FONT]. 

But I suggest that you move your executable files to ~/bin unless you use them very seldom and and get along with ```
bash script.bash
``` or ```
sh script.sh
```.

---

### Post by MikeCyber on 2012-12-21
Thanks, you are saying adding this:

#UUID=58E0EFA0E0EF831C /media/Win-F                        ntfs    defaults        0       0

would allow to execute with ./script.sh
Well, I might try. Anyway using sh script.sh is the same amount of numbers to type.

---

### Post by sudodus on 2012-12-21
I think your suggestion for /etc/fstab would work (without the # sign), otherwise look at this link

[[COLOR="Red"]http://askubuntu.com/questions/120233/cant-mount-ntfs-partition-without-root-access[/COLOR]]("http://askubuntu.com/questions/120233/cant-mount-ntfs-partition-without-root-access")

Such a line (specifying read/write permission with rw) should help:

```
UUID=58E0EFA0E0EF831C  /media/Win-F  ntfs  nls=iso8859-1,rw,umask=000,user  0  0
```

Remove the # sign, it 'comments the line away', so that it will not be used, only sits there for you to read as a help text 'a comment'.

---

### Post by MikeCyber on 2012-12-21
Yes thanks that works. 
I need that also because I call another app(not sh) ./blaa within the script.

---

### Post by sudodus on 2012-12-21
I'm glad it works for you :-)

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED!

---

