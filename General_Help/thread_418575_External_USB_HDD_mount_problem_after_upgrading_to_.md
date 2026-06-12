---
title: "External USB HDD mount problem after upgrading to feisty!"
date: 2007-04-22
forum: General Help
---

### Post by Dark_Master on 2007-04-22
[FONT="Comic Sans MS"][SIZE="4"][COLOR="RoyalBlue"]
Hey all, I recently upgraded from Edgy to Feisty. however that induced some problems, all could be worked around, except for this, I am using an external USB storage device (Western Digital) and I had no problems with it in edgy. However, now it does not mount automatically (nor does ANY usb device mount automatically), I know the system can see it because when I go to media:/ I can see it (but it is unmounted) and if I try to click on it or choose to mount it, I get the following error: 
*hal-storage-removable-mount-all-options refused uid 1000*
However, I am able to mount it manually using *pmount-hal /dev/sdbX"*

Another thing, my internal HDD was seen in edgy as hdaX, but now it is seen as sdaX!
[/COLOR][/SIZE][/FONT]

---

### Post by taurus on 2007-04-22
Plug in the external harddrive (and don't forget to turn it on if there is a power button) and post the output of this command here.

```
sudo fdisk -l
```

p.s.  What's up with the font size and color?

---

### Post by Dark_Master on 2007-04-22
[FONT="Comic Sans MS"][SIZE="1"][COLOR="RoyalBlue"]
Here's everything, obviuosly the second part is the external HDD

[SIZE="1"]Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3187    25599546    7  HPFS/NTFS
/dev/sda2            3188        7649    35841015    5  Extended
/dev/sda3            7650        9561    15358140   83  Linux
/dev/sda4            9562        9729     1349460   82  Linux swap / Solaris
/dev/sda5            3188        7012    30724281    7  HPFS/NTFS
/dev/sda6            7013        7649     5116671    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       12748   102398278+   7  HPFS/NTFS
/dev/sdb2           19760       32507   102398310    7  HPFS/NTFS
/dev/sdb3           32508       60801   227271555    f  W95 Ext'd (LBA)
/dev/sdb5           32508       40156    61440561    7  HPFS/NTFS[/SIZE]

P.S. The font size is 4 and the color is "RoyalBlue" ;)
[/COLOR][/SIZE][/FONT]

---

### Post by taurus on 2007-04-22
Your external harddrive is now known as /dev/sdb.

If you want to access those partitions, you need to mount them first from a terminal.

```
sudo mkdir /media/sdb1 /media/sdb2 /media/sdb5
sudo mount -t ntfs /dev/sdb1 /media/sdb1 -o nls=utf8,umask=0222
sudo mount -t ntfs /dev/sdb2 /media/sdb2 -o nls=utf8,umask=0222
sudo mount -t ntfs /dev/sdb5 /media/sdb5 -o nls=utf8,umask=0222
df -h
```

---

### Post by Dark_Master on 2007-04-22
[FONT="Comic Sans MS"][SIZE="4"][COLOR="RoyalBlue"]
I know I can mount them using the terminal, but this is not what I wanted. You see, in edgy I needn't do that, whenever I plugged it in (or booted with it plugged in) it would be mounted automatically!

P.S. Something wrong with my font size??
[/COLOR][/SIZE][/FONT]

---

### Post by laxon on 2007-04-22
Hey Guys,

I have the same problem. I can see my external harddrive using fdisk -l and I can manually mount them. But under edgy it used to be possible that it mounts automatically. And in the "System - Preferences - Removable Drives and Media" it is set to automount (when hotplugged). I have a clean feisty 64 bit installation on my computer.

Any suggestions?

Thanks
Alex

---

### Post by json684 on 2007-04-23
Any help out there? I am having the same problem. pmount /dev/sdb1 mounts just fine but if I try to mount the usb hard drive through konqueror I get 

hal-storage-removable-mount-all-options refused uid 1000

With Kubuntu Feisty as my distro. It is more of a matter of wanting it to just plug in without having to mess with fstab and what not. Any help would be appreciated.

Edit: And now for another problem. I mount just fine with pmount /dev/sdb1, but I dont have write permissions just read.

---

### Post by strabes on 2007-04-23
I thought I would answer your other question. All types of storage devices are now referred to as sda* instead of both sda* and hda*. It just simplifies things all around.

---

### Post by moore.bryan on 2007-04-23
> **strabes said:**
> I thought I would answer your other question. All types of storage devices are now referred to as sda* instead of both sda* and hda*. It just simplifies things all around.
[I]this got me too... someone around these here forums set me straight: apparently the sata/scsi drivers are better, so no more hda, hdb, hdc...

my external western digital hd is permanently connected to my computer for storage, so i put an entry in fstab for it.  for my usb flash drives, i use ivman (it's in the repos) to handle everything.
[/I]

---

### Post by Dark_Master on 2007-04-24
[FONT="Comic Sans MS"][SIZE="4"][COLOR="RoyalBlue"]
obviously this is a common problem!! hasnt anyone figured out a solution yet?

As for me, my exteranl HDD is usually connected, but since I'm using a laptop, its not always there!!
[/COLOR][/SIZE][/FONT]

---

### Post by moore.bryan on 2007-04-24
> **Dark_Master said:**
> [FONT=Comic Sans MS][SIZE=4][COLOR=RoyalBlue]
obviously this is a common problem!! hasnt anyone figured out a solution yet?

As for me, my exteranl HDD is usually connected, but since I'm using a laptop, its not always there!!
[/COLOR][/SIZE][/FONT]
*ivman works for me (it's in the repos).*

---

### Post by Dark_Master on 2007-04-24
> **moore.bryan said:**
> *ivman works for me (it's in the repos).*

[FONT="Comic Sans MS"][SIZE="4"][COLOR="RoyalBlue"]
tried it, but didnt solve the problem. As a matter of fact, it caused more problems :( 
[/COLOR][/SIZE][/FONT]

---

### Post by moore.bryan on 2007-04-24
> **Dark_Master said:**
> [FONT=Comic Sans MS][SIZE=4][COLOR=RoyalBlue]
tried it, but didnt solve the problem. As a matter of fact, it caused more problems :( 
[/COLOR][/SIZE][/FONT]
*"more problems?"  how so?*

---

### Post by GoodPanos on 2007-04-24
Me too.  I installed it and I don't see it any where in my menus.  When I run it in konsole I get the following:
```
manager.c:1362 (do_startup_configure) Directory /home/panos/.ivman/ will be used for configuration files.
```...and then it just sits there.

But you should not have to install ivman.  It should just work.  There must be a bug with Kubuntu, because it works fine in Ubuntu.:???:

---

### Post by moore.bryan on 2007-04-25
> **GoodPanos said:**
> Me too.  I installed it and I don't see it any where in my menus.  When I run it in konsole I get the following:
```
manager.c:1362 (do_startup_configure) Directory /home/panos/.ivman/ will be used for configuration files.
```...and then it just sits there.

But you should not have to install ivman.  It should just work.  There must be a bug with Kubuntu, because it works fine in Ubuntu.:???:
*you don't need to "run it," it runs itself as a daemon.  once you install it, it's running; just try to plug-n-play.*

---

### Post by l_b on 2007-04-25
I'm having the same problems....

Edgy Eft + IVman = good
Feisty Fawn + IVman = bad

mounting it by hand works flawless. But Ivman does nothing at all.

---

### Post by moore.bryan on 2007-04-26
> **l_b said:**
> I'm having the same problems....

Edgy Eft + IVman = good
Feisty Fawn + IVman = bad

mounting it by hand works flawless. But Ivman does nothing at all.
*i'm using ivman in feisty and it works flawlessly for me.  any error messages?*

---

### Post by GoodPanos on 2007-04-26
> **moore.bryan said:**
> *i'm using ivman in feisty and it works flawlessly for me.  any error messages?*
Okay, but which distro, Ubuntu or Kubuntu?  I know read/write works fine even without ivman on Ubuntu but the difficulties reported here are from Kubuntu, at least mine are.

---

### Post by moore.bryan on 2007-04-26
[I]i use openbox, so i don't have gnome/kde installed... afaik that makes it ubuntu.  i do, however, have both gnome and kde programs installed, so i would think if that were the issue it would show-up on my system, too.

as i asked, are there any errors?  what exactly happens when you plug something in?
[/I]

---

### Post by size_XXM on 2007-04-28
Almost the same problem here [Kubuntu Feisty, new install] - I have a USB drive, partitioned into one NTFS partition and one FAT32 partition. When I plug it in, both partitions are recognized and KDE Daemon appears for both of them. However, only the FAT partition is mounted in a folder named by it's volume label. When I explore the NTFS volume, it's just not mounted, no errors. After I manually run **pmount /dev/sdc1**, the volume is mounted using plain ntfs (and it's read-only).

As for /etc/fstab, that contains no entries for partitions of removable drives.

Is this a problem with pmount? Or maybe the ntfs-3g configuration?

BTW, same problem with yet another "install-this-package fix" (kwikdisk) is discussed on [kubuntuforums.net]("http://kubuntuforums.net/forums/index.php?topic=3082392.0")

FIXED: wrong link

---

### Post by Acejam on 2007-04-29
I've had this same problem.

I have an external harddrive that uses USB of FireWire, I happen to use the FireWire method.

After reading one of the links posted in this thread (the one above I think) it seems the following works for me, and allows me as a "user" to view the drive when I mount it using a "sudo".

**sudo pmount /dev/sdb1**

Hope that helps!

---

### Post by Drenhead on 2007-04-29
when I try sudo pmont /dev/sdh1
it tells me "you do not have enough permissions to read file:///media/sdh1

Any suggestions?

---

### Post by Drenhead on 2007-04-29
I am able to mount it when I do this command:

sudo mount -t ntfs /dev/sdh1 /media/sdh1 -o nls=utf8,umask=0222

This makes it where I can read it, but I can't delete or write anything to it.  What do I have to do for that?

---

### Post by json684 on 2007-04-29
> **Drenhead said:**
> I am able to mount it when I do this command:

sudo mount -t ntfs /dev/sdh1 /media/sdh1 -o nls=utf8,umask=0222

This makes it where I can read it, but I can't delete or write anything to it.  What do I have to do for that?

First you need to make sure the ntfs-3g driver is installed. You can use
```

sudo apt-get install ntfs-3g ntfs-config

```

Then run ntfs-config and select the enable writing to internal drives and external drives. And then in your command change ntfs to ntfs-3g. That should work. Still waiting on a automount fix though. :)

---

### Post by Drenhead on 2007-04-30
Sorry, but that didn't work.  Still tells me I don't have authority.

Any more suggestions?

---

### Post by json684 on 2007-04-30
What part told you you didnt have authority? You ran ntfs-config after installing ntfs-3g right? ntfs-config does need to run with sudo. Sorry I can't help more.

---

### Post by SamChameleon on 2007-05-02
I had a similar problem. My external USB HDD was not found at all. Only when repeating the "lsmod" command the drive was found and automounted, but soon after lost again. Command "dmesg" showed this:

```

[ 1615.003383] usb 3-1: new high speed USB device using ehci_hcd and address 38
[ 1615.115206] usb 3-1: device descriptor read/64, error -71
[ 1615.330869] usb 3-1: device descriptor read/64, error -71
[ 1615.546519] usb 3-1: new high speed USB device using ehci_hcd and address 39
[ 1615.658338] usb 3-1: device descriptor read/64, error -71
[ 1615.873991] usb 3-1: device descriptor read/64, error -71
[ 1616.089652] usb 3-1: new high speed USB device using ehci_hcd and address 40
[ 1616.497008] usb 3-1: device not accepting address 40, error -71
[ 1616.608846] usb 3-1: new high speed USB device using ehci_hcd and address 41
[ 1617.016192] usb 3-1: device not accepting address 41, error -71
[23508.333683] usb 3-1: new high speed USB device using ehci_hcd and address 42
[23508.453492] usb 3-1: device descriptor read/64, error -71
[23508.677134] usb 3-1: device descriptor read/64, error -71
[23508.896780] usb 3-1: new high speed USB device using ehci_hcd and address 43
[23509.016591] usb 3-1: device descriptor read/64, error -71
[23509.240242] usb 3-1: device descriptor read/64, error -71

```

So I tried to reload the driver and it worked: 
```

modprobe -r ehci_hcd

```

Perhaps this helps.

---

### Post by azarhal on 2007-05-02
> **SamChameleon said:**
> I had a similar problem. My external USB HDD was not found at all. Only when repeating the "lsmod" command the drive was found and automounted, but soon after lost again. Command "dmesg" showed this:

```

[ 1615.003383] usb 3-1: new high speed USB device using ehci_hcd and address 38
[ 1615.115206] usb 3-1: device descriptor read/64, error -71
[ 1615.330869] usb 3-1: device descriptor read/64, error -71
[ 1615.546519] usb 3-1: new high speed USB device using ehci_hcd and address 39
[ 1615.658338] usb 3-1: device descriptor read/64, error -71
[ 1615.873991] usb 3-1: device descriptor read/64, error -71
[ 1616.089652] usb 3-1: new high speed USB device using ehci_hcd and address 40
[ 1616.497008] usb 3-1: device not accepting address 40, error -71
[ 1616.608846] usb 3-1: new high speed USB device using ehci_hcd and address 41
[ 1617.016192] usb 3-1: device not accepting address 41, error -71
[23508.333683] usb 3-1: new high speed USB device using ehci_hcd and address 42
[23508.453492] usb 3-1: device descriptor read/64, error -71
[23508.677134] usb 3-1: device descriptor read/64, error -71
[23508.896780] usb 3-1: new high speed USB device using ehci_hcd and address 43
[23509.016591] usb 3-1: device descriptor read/64, error -71
[23509.240242] usb 3-1: device descriptor read/64, error -71

```

So I tried to reload the driver and it worked: 
```

modprobe -r ehci_hcd

```

Perhaps this helps.

Thanks a lot, I had the same error and that fixed my problem. :)

---

### Post by SamChameleon on 2007-05-03
Glad I could help :)  But there is still a problem: I have to reload the driver manually after each reboot. That`s not a great problem, but disturbing anyway. Has anybody a suggestion of what is wrong with driver "ehci-hcd"??

---

### Post by Dark_Master on 2007-05-12
[FONT="Comic Sans MS"][SIZE="4"][COLOR="RoyalBlue"]
YAAAAAAAAAY, finally solved that pesky problem, all it needs is to just add the correct lines to the */etc/fstab* file

I added something like:
/dev/sdbX   /media/<Location>   ntfs-3g   defaults,users,sync,locale=en_US.UTF-8 0 1

For each parition on my external HDD, and now everthing works just fine, it mounts automatically when I plug it in, and I can unmount it at wish!!
[/COLOR][/SIZE][/FONT]

---

