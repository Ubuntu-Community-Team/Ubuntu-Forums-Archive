---
title: "How to mount USB drive with full permissions"
date: 2016-09-22
forum: General Help
---

### Post by Transcix on 2016-09-22
Hello and thanks very much in advance for any assistance. Although I'm a smart person I don't have time to learn everything about computers, and while I know enough thankfully to know that Ubuntu is much better than Windows, I'm not convinced that Ubuntu is for me because unfortunately the circumstances of my life don't give me much time to learn everything about Ubuntu. While I've extensively Googled my current problem for a couple hours, potential solutions have either not functioned or lie beyond my understanding and capabilities. While I refuse to switch away from Ubuntu for such a simple problem, I also refuse to believe that a simple solution doesn't exist, in which case I must question how solutions are aggregated but that's a separate issue.

I purchased a USB stick by Verbatim of 32GB. It worked fine in the past but now it says that I can't write anything to it because it's "read-only". When I open the files folder thing and right-click on the USB stick and access "properties", the "permissions" drop-down menus are all greyed-out, and under "local network share" I'm able to click "share this folder" and save the changes but if I click "allow others to create and delete files in this folder" then I'm unable to save the changes, instead it gives me the message:

> Nautilus needs to add some permissions to your folder "usb-Verbatim_STORE_N_GO_o70B54DF91F70138-0:0-part1" in order to share it. The folder "usb-Verbatim_STORE_N_GO_o70B54DF91F70138-0:0-part1" needs the following extra permissions for sharing to work: - write permissions by others Do you want Nautilus to add these permissions to the folder automatically?

When I click "add the permissions automatically" then I receive the following error message:

> Could not change the permissions of folder "usb-Verbatim_STORE_N_GO_o70B54DF91F70138-0:0-part1"

So basically this is where I am. My Ubuntu version is up-to-date and I formatted the USB drive to fat32 with gparted.

I've encountered countless Ubuntu errors and glitches in the past days and have spent hours on this issue, so I'll be most grateful to anyone who can finally provide a solution. It shouldn't be this hard.

---

### Post by sudodus on 2016-09-23
In order to help we need to know more about your USB drive. So please

- run the following command lines in a terminal window,

```
df -h
sudo parted -ls
sudo lsblk -f
sudo lsblk -m
ls -ld /media
ls -l /media
ls -l /media/$USER
```

- copy and paste them into a reply window (here), you can do it by marking with the left mouse button pressed, and pasting (here) with the middle button (or pressing the wheel).

- click on the big red button 'Go Advanced',

- mark the copied text and click on the # icon above the window to put it within CODE tags.

- and send the reply :-)

---

### Post by Transcix on 2016-09-23
Thanks Sudodus, here's the information:

df -h:
```
Filesystem      Size  Used Avail Use% Mounted on
udev            1.8G     0  1.8G   0% /dev
tmpfs           364M   11M  353M   3% /run
/dev/sda4       440G   33G  385G   8% /
tmpfs           1.8G  604K  1.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           1.8G     0  1.8G   0% /sys/fs/cgroup
/dev/sda1       511M  3.6M  508M   1% /boot/efi
cgmfs           100K     0  100K   0% /run/cgmanager/fs
tmpfs           364M   68K  364M   1% /run/user/1000
/dev/sda2       474G   28G  423G   7% /media/simard/af583240-1afc-4fdf-b7ad-82fefecdae8f
/dev/sdb1        29G   16K   29G   1% /mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1

```

sudo parted -ls:
```
Model: ATA WDC WD10EZEX-60M (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name  Flags
 1      1049kB  538MB   537MB   fat32                 boot, esp
 2      538MB   517GB   516GB   ext4
 4      517GB   996GB   479GB   ext4
 3      996GB   1000GB  3957MB  linux-swap(v1)


Model: Verbatim STORE N GO (scsi)
Disk /dev/sdb: 31.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  31.0GB  31.0GB  primary  fat32        boot

```

sudo lsblk -f:
```
NAME   FSTYPE LABEL UUID                                 MOUNTPOINT
sda                                                      
&#9500;&#9472;sda1 vfat         3E67-B07C                            /boot/efi
&#9500;&#9472;sda2 ext4         af583240-1afc-4fdf-b7ad-82fefecdae8f /media/simard/af583240-
&#9500;&#9472;sda3 swap         7999b844-0767-4d7a-8b1b-af039772576b [SWAP]
&#9492;&#9472;sda4 ext4         dded6fd4-2f0b-4607-a3f5-294fd098403f /
sdb                                                      
&#9492;&#9472;sdb1 vfat         DE8E-95AA                            /mnt/usb-Verbatim_STORE
sr0                           

```

sudo lsblk -m
```
NAME     SIZE OWNER GROUP MODE
sda    931.5G root  disk  brw-rw----
&#9500;&#9472;sda1   512M root  disk  brw-rw----
&#9500;&#9472;sda2   481G root  disk  brw-rw----
&#9500;&#9472;sda3   3.7G root  disk  brw-rw----
&#9492;&#9472;sda4 446.4G root  disk  brw-rw----
sdb     28.9G root  disk  brw-rw----
&#9492;&#9472;sdb1  28.9G root  disk  brw-rw----
sr0       40M root  cdrom brw-rw----

```

ls -ld /media
```
drwxr-xr-x 4 root root 4096 Sep 22 17:28 /media
```

ls -l /media
```
total 8
drwxr-xr-x  2 root root 4096 Sep 22 17:28 Datas
drwxr-x---+ 3 root root 4096 Sep 22 17:04 simard

```

ls -l /media/$USER
```
total 4
drwxr-xr-x 24 root root 4096 Feb 28  2016 af583240-1afc-4fdf-b7ad-82fefecdae8f

```

---

### Post by sudodus on 2016-09-23
It looks like you have mounted the pendrive's FAT partition /dev/sdb1 on /mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1

And it looks like you need 'more permissions'. Microsoft file systems (FAT and NTFS) get the permissions permanently at the mount, and cannot be modified.

So what you should do is mount the pendrive's FAT partition with read and write permissions

You can use the mount command line tool. From ```
man mount
``` you can find

```
       -w, --rw, --read-write
              Mount the filesystem read/write.  This is the default.  A synonym is -o rw.

       users  Allow any user to mount and to unmount the filesystem, even when some other  ordinary  user  mounted  it.   This
              option  implies the options noexec, nosuid, and nodev (unless overridden by subsequent options, as in the option
              line users,exec,dev,suid).

       umask=value
              Set the umask (the bitmask of the permissions that are not present).  The default is the umask  of  the  current
              process.  The value is given in octal.
```

So unmount the partition

```
sudo umount /dev/sdb1
```

and mount it with read/write permissions (if the mount point directory still exists, otherwise create a new mount-point)

```
sudo mount -o [COLOR="#cc0000"]rw,users,umask=000[/COLOR] /dev/sdb1 /mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1
```

Now, at least, you should be able to write to the directory via sudo command lines, for example

```
cd /mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1
sudo bash -c "echo 'Hello World' > hello.txt"

cat hello.txt  # this command should print the output of the file, 'Hello World' (without quote characters).
```

The next step is to try with Nautilus. If it works, please click on **Thread Tools** at the top of the page and mark this thread as SOLVED :-)

Otherwise tell us what happened, and we will try some more tweaks.

---

### Post by Transcix on 2016-09-23
Thanks Sudodus, your solution worked perfectly. I would never have been able to figure that out by myself so I really appreciate it!

---

### Post by Transcix on 2016-09-23
Woops, it appears the celebration was premature. The USB flash drive was working for a few hours and I transferred various files to it, but now when I insert it into the USB port I receive the following error message:

> 
Unable to mount 31 GB Volume

Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1"' exited with non-zero exit status 32: mount: /dev/sdb1 is already mounted or /mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1 busy
       /dev/sdb1 is already mounted on /mnt/usb-Verbatim_STORE_N_GO_070B54DF91F70138-0:0-part1


I don't know if the "busy" at the end of the second line should be immediately followed by the "/dev" at the beginning of the third line or if there should be a space.

I tried inserting the USB a few times and restarting the computer but the problem persists.

I can transfer files from the USB to the computer, but I can't add files from the computer to the USB.

On a side note, this sure would be easier if the darn USB drive had a shorter name.

---

### Post by sudodus on 2016-09-24
Maybe you have problems because you unplugged the pendrive without unmounting it. This can make the file system corrupted. See this link, which describes how to repair it: [Repair the partition table and file system of a pendrive](http://ubuntuforums.org/showthread.php?t=2196858&p=13409986#post13409986)

-o-

You can create a shorter name :-) The ***label*** of a partition is often used as a name. You can use ***gparted*** to create/change a label. It comes with the Ubuntu family iso files and is available directly in the live systems 'Try Ubuntu, Kubuntu, Lubuntu, ... Xubuntu', but you can install it into an installed system

```
sudo apt-get install gparted
```

But independent of the label you can create mountpoints with a shorter name, for example usb1, usb2 ...

So unmount the partition using the device name

```
sudo umount /dev/sdb1
```

and create the new mountpoint (only once)

```
sudo mkdir /mnt/usb1
```

and mount it with read/write permissions

```
sudo mount -o [COLOR="#cc0000"]rw,users,umask=000[/COLOR] /dev/sdb1 /mnt/usb1
```

Now you can also unmount it using the mount point, which should be more precise, because that device name might differ,

```
sudo umount /mnt/usb1
```

---

### Post by sudodus on 2016-09-24
You can also ***mount*** a partition with a unique label ***via the label***. This is often done by the automatic mounting system, that works in many cases. Maybe you don't want the automatic mounting, when using it as a "local network share", but you want a fixed mount point, which is described in the previous post.

Anyway, this is an alternative:

We assume that you used ***gparted*** to add the label **Verbatim1** to the partition on the pendrive. Now you can mount it like this:

```
sudo mount -o rw,users,umask=000 -L Verbatim1 /mnt/usb1
```

---

### Post by Transcix on 2016-09-25
Thanks again Sudodus. I didn't realize I should unmount my USB drive before removing it, which might explain why many of my other USB drives also suffer from a range of issues. I tried ardently to follow your most-appreciated instructions but it just didn't work for whatever reason, despite several attempts and a few Google consultations. I couldn't even rename the darn thing, I mean I renamed the file system but then I discovered I had to rename the partition and once I renamed that then there was still the "id" or something that was still the original annoyingly long name and it would always default to that long name, anyways. I'm sure your advice was correct but I just wasn't fully able to connect the dots in applying it. I was about to give up but then it occurred to me that, if this USB drive stuff is really so complex, there might be some software to make it easier for the layperson, and I found "Disks" which quickly fixed all my problems! I'm sorry this thread consumed so much of your time, I'll try to be more clear in the future because I'm sure you would have pointed "Disks" out to me, I guess you must have assumed that since it's such a common piece of software I must already know of it. I've at least learned some important tips from your replies and your efforts are much appreciated, take care Sudodus.

---

### Post by gacb on 2017-02-17
As I tend to use GUI solutions to pass on to Windows refugees, I solved it with Nautilus via the administrative plugin available in Synaptic. Opening the Properties in administrative mode allows one to change permissions from root to your username as well as for Group and Others.

---

### Post by MikeCyber on 2017-06-10
ps: solved. usb startup disk creator does something wrong.
delete all partitions and redo in gparted:
sudo sgdisk --zap-all /dev/sdd

-----

hmm tried all kind of stuff without luck. How to do it easily with
sudo gnome-disks
?
Thanks
drw-rw-rw-   2 root    root     4096 Jun 10 12:58 usb-_USB_DISK_2.0_07961501647A066E-0:0-part1
ps: this is a ubuntu install usb created with start disk creator

---

### Post by sudodus on 2017-06-10
@MikeCyber,

Which version of usb-creator-gtk (alias Startup Disk Creator)?

Check with

```
apt-cache policy usb-creator-gtk
```

Alternatively, which version of Ubuntu? Explanation: The Startup Disk Creator was changed from an extracting tool (version 0.2.23) to a cloning tool (version 0.3.2) in Ubuntu version 16.04 LTS.

The new version of the Startup Disk Creator creates a very different USB boot drive compared the older versions. The cloned drive has a hybrid iso9660 file system which works in both DVD drives and USB drives, memory cards and other mass storage devices. The iso 9660 file system is read-only by design.

If you want to edit the file system, or if you want a read-write file system, you should use an extracting tool, for example Rufus in Windows or make a persistent live drive with mkusb. (But mkusb clones the iso file to make live-only boot drives, so live-only drives by mkusb will be like the drives made by the Ubuntu Startup Disk Creator).

---

