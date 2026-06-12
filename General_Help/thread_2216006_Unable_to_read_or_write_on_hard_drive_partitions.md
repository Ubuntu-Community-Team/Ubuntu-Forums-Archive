---
title: "Unable to read or write on hard drive partitions"
date: 2014-04-09
forum: General Help
---

### Post by omar13 on 2014-04-09
So, I've just installed Lubuntu 13.10 on an old machine, and I'm totally new to Linux generally, I've been using Windows ever since, so when I try to open the drives *except for the on I have installed Lubuntu on* it requests the password to mount it, then I try to access files on it, I get this error: "Error opening directory '/media/username/UUID' Permission denied.
And on startup screen it says: "The disk drive *code* is not ready yet or present, Continue to wait, press S to skip mounting or M for manual recovery".
Help?
[UPDATE] I only mounted the first partition which I installed the OS on manually when partitioning my hard drive with gparted live.

---

### Post by ajgreeny on 2014-04-09
To help you further we need to know exactly what partitions you have on disk in your machine, so please open a terminal and run the command ```
sudo fdisk -l
``` and report back here with the output you get.  Then run command ```
sudo blkid -c /dev/null
``` and finally ```
cat /etc/fstab
``` and again show us the output from those two.

That should mean we can show you a way to mount the partitions automatically at boot, and be able to read and write to them by making an edit to the fstab file you show us.

---

### Post by omar13 on 2014-04-10
First, thank you for the quick response.
So, that's what I got: 
```
sudo fdisk -l
```

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00008ddf

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   146485247    73241600   83  Linux
/dev/sda2       146485248   151093247     2304000   82  Linux swap / Solaris
/dev/sda3       151093248   563931135   206418944   83  Linux
/dev/sda4       563931136   976769023   206418944   83  Linux


```

```
sudo blkid -c /dev/null
```

```
/dev/sda1: UUID="6f3b5e1f-688f-4caf-81aa-d307b74ee682" TYPE="ext4"
/dev/sda2: UUID="28ce9947-f7b1-4854-9839-880b7a0ebf8b" TYPE="swap"
/dev/sda3: UUID="4ce42dbe-e7c6-40eb-bb6e-9769506966d1" TYPE="ext4"
/dev/sda4: UUID="c380a7db-207d-4f80-ace4-d1a1e431ab96" TYPE="ext4"
/dev/zram0: UUID="7487af7a-71cb-480e-96e9-c6112555c42c" TYPE="swap"
/dev/zram1: UUID="8b8813eb-4b69-44ec-9989-7a5c9f9b092d" TYPE="swap"


```

```
cat /etc/fstab
```

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=6f3b5e1f-688f-4caf-81aa-d307b74ee682 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a4bb24b7-b468-4725-a195-fac5c1a80431 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

```

---

### Post by Bashing-om on 2014-04-10
omar13; Hi !

While I am passing by, allow me to assist.
Your swap UUIDs do not match:
What is:
> 
/dev/sda2: UUID=[color=blue]"28ce9947-f7b1-4854-9839-880b7a0ebf8b"[/color] TYPE="swap"

as to what is in error; -> your /etc/fstab file:
> 
#swap was on /dev/sda5 during installation
UUID=[color=red]a4bb24b7-b468-4725-a195-fac5c1a80431[/color] none            swap    sw              0       0


My suggestion: -> edit the File System TAble to reflect what is true:
Make a back up of the current file, just because Murphy's law always applies:
```

sudo cp /etc/fstab /etc/fstab-10apr2014

```
Fire up your favorite text editor - here gedit -:
```

gksudo gedit /etc/fstab

```
and make the following edits:
"swap was on /dev/sda5 during installation" -> swap has been moved to sda2 10apr2014
" UUID=a4bb24b7-b468-4725-a195-fac5c1a80431 " -> UUID=28ce9947-f7b1-4854-9839-880b7a0ebf8b

copy and paste for best results.

save the file and exit back to terminal.
Check for error prior to rebooting;
What returns from the terminal command:
```

mount -a

``` a no return is a good thing - system did as told, no back talk. Else if a problem will talk to you about it.

Now IF there are no errors reported, reboot and lets see the effect.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by ajgreeny on 2014-04-11
For some reason you also appear to have one partitioned swap, sda2, and two zram compressed swapfiles, zram0 and zram1, on your system; why is that?

---

### Post by walterorlin on 2014-04-12
zram0 and zram are enabled by default in lubuntu 13.10 so that is why they are there not sure everyone knows that.

---

### Post by ajgreeny on 2014-04-12
Well thanks.

I was certainly not aware of that, but having just run blkid in my Lubuntu trusty, there it is!

---

### Post by bapoumba on 2014-04-12
> **ajgreeny said:**
> Well thanks.

I was certainly not aware of that, but having just run blkid in my Lubuntu trusty, there it is!

+1!

---

### Post by omar13 on 2014-04-14
Hey there,
I tried to launch gedit but it says that it's not installed. And I couldn't edit fstab using LeafPad.
Should I download and install gedit manually?

---

### Post by Bashing-om on 2014-04-14
omar13; Hello.

I have not used 'leafpad' in ages, but to the best of my remembrance one has to right click on the file and choose "open as root".
Installing 'gedit', would bring in a lot of probably unwanted libraries, themes  and related files. Most likely on a lightweight system not what you want to do,

Else: there is always the default CLI editor 'nano'; with but a bit of research to learn how to use it, will get the job done.

[INDENT]I do hope this helps
[/INDENT]

---

### Post by ajgreeny on 2014-04-14
Not sure if the right click "open as root" is still available in pcmanfm in 13.10 but it has certainly disappeared in 14.04, so you'll need to use ```
gksudo leafpad /etc/fstab
``` to edit the file.  You may even have to install gksu to do so, as I'm not sure gksu is installed by default.
You can also use ```
sudo nano /etc/fstab
``` to edit it with the command line editor nano.

---

### Post by omar13 on 2014-04-16
Did what Bashing-om said, problem persists, but the message on startup disappeared.

---

### Post by Bashing-om on 2014-04-16
omar13; Well !

Show us:
```

cat /etc/fstab
sudo apt-get update
sudo apt-get upgrade

``` and we will see
[INDENT][INDENT]what tale is told
[/INDENT][/INDENT]

---

