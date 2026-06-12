---
title: "tun2fs problem"
date: 2021-08-15
forum: General Help
---

### Post by jgw on 2021-08-15
I have a tune2fs problem.
I did a "tune2fs -L dune /dev/sda1" and then a "tune2fs -l /dev/sda1 | grep volume" to see it it worked, yesterday.  It told me it had.

Today I thought I would check with "tune2fs -l /dev/sda1 | grep volume"  It didn't, was still /dev/sda1.  I then tried to change the name again and got an error message.  Did it later and, this time, there was no error message so I checked the name again.  This them it get me:
tune2fs: Permission denied while trying to open /dev/sda1
Couldn't find valid filesystem superblock.

I am, basically, back to where I started unless somebody can tell me what I did wrong.

Thank you.............

---

### Post by Bashing-om on 2021-08-15
jgw; Hey

Try putting the label within quotes.
```

sundo tune2fs -L "dune" /dev/sda1

```

[INDENT]that's the way
[INDENT]I do it
[/INDENT][/INDENT]

---

### Post by oldfred on 2021-08-15
[FONT=monospace][FONT=arial]What does this show?  There is no space in mountpoint, forum is not helping. Tried different fonts, saving & reposting, but...
lsblk -e 7 -o name,fstype,size,model,fsused,label,partlabel,mountpoint,partuuid

If you post it be sure to use code tags.
Easy to add with # icon in Forum's advanced Editor.

[/FONT][/FONT]

---

### Post by jgw on 2021-08-17
oldfred - thanks for the reply.

are you telling me to enter "lsblk -e 7 -o name,fstype,size,model,fsused,label,partlabel,moun tpoint,partuuid" in the terminal?
"

---

### Post by jgw on 2021-08-17
Bashing-om - thanks for the reply!

I did as you said.  What that did was to change the name in files but ignored the name which remains the same, ie "/dev/sda1"  I have no idea where it gets its info.

disks tells me that the name is "dev/sda1" and the uuid is: "8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4"

This remains a real mystery...........

---

### Post by sudodus on 2021-08-17
1. Please try to copy and paste the following command line into a command line window (terminal window) and run it by pressing the Enter key:

```

lsblk -e 7 -o name,fstype,size,model,label,partlabel,mountpoint,partuuid

```

(It seems that the forums website works better now (compared to when oldfred tried to get things correct).

2. And then, please copy the output from the command line window (terminal window) and paste it into an editing window here and put code tags around it to render it as code to make it easier to read:

[noparse]```

output

```[/noparse]
 
to get output like this
 
```

output

```

---

### Post by jgw on 2021-08-17
```
artuuid
NAME FSTYPE  SIZE MODEL LABEL PARTLABEL MOUNTPOINT PARTUUID
sda          3.6T ST400                            
&#9492;&#9472;sda1
     ext4    3.6T       data  data_up   /mnt/8ccdc fde78524-e948-41f1-9865-3e8d0956900d
sdb          2.7T Hitac                            
&#9500;&#9472;sdb1
&#9474;              1M                                  6bb0b4f0-986d-49b4-91be-5a559b78925c
&#9500;&#9472;sdb2
&#9474;    vfat    513M             EFI System Partition
&#9474;                                       /boot/efi  33312758-043a-458e-95d6-a3633151b4e5
&#9492;&#9472;sdb3
     ext4    2.7T                       /          b8bb47ac-49cc-4181-9d84-7fea61b56250
sr0         1024M PLDS_                            

```

---

### Post by ajgreeny on 2021-08-17
You have not shown that you used sudo for your ***tune2fs -L ***command but surely to label a partition requires root permissions?

---

### Post by TheFu on 2021-08-17
**tune2fs** always needs a **sudo**.
Setting a label won't change the /dev/sd-whatever.  It just sets a label.  That label can be used to mount it instead of using a UUID or as a human-readable reminder. Not many other uses. Did you expect something else to happen?

Manpage:
```
       -L volume-label
              Set the volume label of the filesystem.  Ext2 filesystem labels can be at most
              16 characters long; if volume-label is longer than 16 characters, tune2fs will
              truncate  it  and  print a warning.  The volume label can be used by mount(8),
              fsck(8), and /etc/fstab(5) (and possibly others) by  specifying  LABEL=volume-
              label instead of a block special device name like /dev/hda5.
```

---

### Post by jgw on 2021-08-17
Thanks for the reply........

That was done with sudo, sorry, I copied what we had, put it in terminal and then backspaced to front and added sudo.  I do know, however, that there is a way to change the uuid because I did it, actually to the same drive, but now everything is changed with the update, etc.  What I really need is to be able to say; "/home/data/, like in cd /home/data/   and have the system go there.   My only other option is to use /home/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4/ which is a bit unwieldy and I would have over 100 to change.  So, basically, I need to change the uuid to 'data' but have no idea how to do that.

I think what I want to do is to somehow set the word "data" to equal the uuid of 8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 so that /home/data/ would be a valid address to use.

---

### Post by TheFu on 2021-08-17
UUIDs aren't LABELs. It doesn't work that way.

If you want something mounted to /home/data, then make an fstab entry that mounts the file system there. No need to use the UUID, if you don't want to. You can use the LABEL instead in the fstab entry. Something like this:

```
LABEL=data  /home/data   ext4   noatime,errors=remount-ro 0 1
```
however, mounting extra storage under /home is a really, really, really bad idea.  Perhaps this is a subtle thing.

Either mount new storage for all of /home:
```
LABEL=HOME  /home   ext4   noatime,errors=remount-ro 0 1
```
or mount extra storage for 1 userid:
```
LABEL=HOME_THEFU  /home/thefu   ext4   noatime,errors=remount-ro 0 1
```

For mounting extra storage to be shared by multiple users, I'd put it somewhere else ... say under /d/ or /opt/d/  then create symbolic links from the user's HOME to that area to make accessing it easy.
There are a few reasons for this, but they are to avoid issues which would likely happen.

Obviously, the labels I've used above would need to exist AND be unique across all mounted storage.   Or you can use the UUID for each.  If you use LVM, there are other, better, options that provide more information.

FYI, look under /dev/disk/by-label/ to see the storage that the mapper process setup automatically.

Chapter 15: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) has more details, if that is needed.

---

### Post by Bashing-om on 2021-08-17
jgw; Huh ?

Sorry, but a bit confused for what you want
> 
What I really need is to be able to say; "/home/data/, like in cd /home/data/ and have the system go there. 

Are you attempting to re-invent the wheel ?
 as that ^ is a function of a mount point.
for instance make a mounting directory - say in /mnt - (can be anywhere)
```

sudo mkdir /mnt/data/ # where "data" resides on a particular partition

```

Then one can use the mount point to access.
```

sudo mount /dev/sdb1 /mnt/data

```

next is to change the ownership from root (as sudo made it so) to you -
```

sudo chown jgw:jgw /mnt/data

```

now a "cd /mnt/data" will make your working directory '/mnt/data'.

As this is manual then the system will expect you to UN-mount when done -
```

sudo umount /mnt/data

```

Be aware to automate the mounting is a function of the /etc/fstab file.

[INDENT][INDENT]like so ?
[/INDENT][/INDENT]

---

### Post by Dennis N on 2021-08-17
_Some terminology and tools:_

file systems get **labels**, and partitions get **names**.
both **labels** and **names** can be created with **gparted**. Only gpt disks can have named partitions.

_Using terminal commands,_
**tune2fs** can label a file system (ext2,3,4 type only).
**e2label** can also label a file system  (ext2,3,4 type only).
**gdisk** can name a partition (but only on GPT partitioned disks)

names remain with partitions, even if you reformat them.
labels on file systems are erased when you reformat.

---

### Post by jgw on 2021-08-19
Thanks for the replies!

Below is my fstab file from my original drive (finally).  This has the solution in the last line.  I'm a bit confused about this one and wonder if I only need the last line or a couple that precede it.  Want to make sure before I copy to my existing fstab file.

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdb2 during installation
UUID=d2904151-d871-4c40-ab61-b584f1955e5f /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sdb1 during installation
UUID=15A4-DED9  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-uuid/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 /media/greg/data/ auto nosuid,nodev,nofail,x-gvfs-show 0 0
```

Thank you..............

---

### Post by TheFu on 2021-08-19
```
[COLOR="#FF0000"]UUID=[/COLOR]8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 /media/greg/data  [COLOR="#FF0000"]auto[/COLOR] nosuid,nodev,nofail,x-gvfs-show 0 [COLOR="#FF0000"]2[/COLOR]
```

Fewer characters means less chance of errors.

Would be best to specify the file system type, not use "auto".
Why mount it in  /media/greg/data?  What's wrong with /media/data?  Longer paths that aren't there for a good reason are just wasted characters.

If you want to know more, man fstab explains what each field is about.  For example:
```
       The sixth field (fs_passno).
              This  field  is  used  by fsck(8) to determine the order in which filesystem
              checks are done at boot time.  The root filesystem should be specified  with
              a fs_passno of 1.  **Other filesystems should have a fs_passno of 2**.  Filesys&#8208;
              tems within a drive will be checked sequentially, but filesystems on differ&#8208;
              ent drives will be checked at the same time to utilize parallelism available
              in the hardware.  Defaults to zero (don't fsck) if not present.

```

---

### Post by jgw on 2021-08-19
Here are the results I got when I added the last line.  /media/greg/data gets me an empty file.  Its pretty strange.  When I am using nautilus, and goto 'data' its the right one but that has always been the case.  I have no idea how that happens whilst there is no data when I do the /media/greg/data then data is empty.  Here are some results:

```

fstab file (last line inserted by system):
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda3 during installation
UUID=bf67ebf9-cf42-4391-b7d9-df6c3da168e3 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda2 during installation
UUID=4E55-8589  /boot/efi       vfat    umask=0077      0       1
/swapfile                                 none            swap    sw              0       0
/dev/disk/by-id/usb-TOSHIBA_HDWD110_20160416-0:0-part1 /mnt/usb-TOSHIBA_HDWD110_20160416-0:0-part1 auto nosuid,nodev,nofail,noauto,x-gvfs-show 0 0
dev/disk/by-uuid/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 /media/greg/data/ ext4 nosuid,nodev,nofail,x-gvfs-show 0 2

/dev/disk/by-uuid/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 /mnt/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 auto nosuid,nodev,nofail,x-gvfs-show 0 0

```
Here is what is in /media/greg/:
```
computer/media/greg/
file:///media/greg/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4
file:///media/greg/d2904151-d871-4c40-ab61-b584f1955e5f
file:///media/greg/data
```

Here is what is in computer (root)/mnt?/:
```
computer/mnt/
x-special/nautilus-clipboard
copy
file:///mnt/usb-TOSHIBA_HDWD110_20160416-0:0-part1
file:///mnt/8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd

```
Here is some terminal stuff.  Put it in to show that 'data' is empty (not what I want):
terminal stuff:
```
greg@movies:/$ cd media
greg@movies:/media$ ls
cdrom  greg
greg@movies:/media$ cd greg
greg@movies:/media/greg$ ls
8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4  data
d2904151-d871-4c40-ab61-b584f1955e5f
greg@movies:/media/greg$ cd data
greg@movies:/media/greg/data$ ls
greg@movies:/media/greg/data$ cd /mnt
greg@movies:/mnt$ ls
8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4  usb-TOSHIBA_HDWD110_20160416-0:0-part1 (last one is external drive)
greg@movies:/mnt$ 

```

I am still not getting to the drive I want to get to.  its the one with the 8ccdc8d0-afeb-4c4b-bb44-9b4e84b7ecd4 UUID that I am shooting at but it gives me a root which is empty.  I thought I would try and boot into /media/greg/ but that failed too (I may have just not known what I was doing)

---

### Post by TheFu on 2021-08-19
I gave you the exact line to add in post #15, but you chose something different which appears to have trivial typos.
Good luck.

BTW, after modifying the fstab file, run these 2 commands to convince systemd to notice the changes:
```
sudo systemctl daemon-reload
sudo mount -a
```

---

### Post by jgw on 2021-08-20
Thank you for the reply!

I have no excuses for what I did, other than the fact that I suspect I didn't pay attention (I'm getting a bit old).  Anyway, I used the one you sent and, it work! I am indebted and, once more, apologize.

Thanks again!

---

### Post by TheFu on 2021-08-20
We are all getting older. Parts ache more today than they did yesterday.  Sleeping through an entire night is a wonderful thing, when it happens.  I'd love to have my eyesight back from 20 yrs ago.

Some of my posts are extremely dense with facts and subtle reasons for doing things a specific way that I don't explain.  And sometimes I show examples, so copy/paste won't work.  Hard for other people to understand, without careful reading.

---

### Post by jgw on 2021-08-22
I copied and pasted what you sent for me to use and, again, it worked!  (previously stated).  It bailed me out of a serious problem which would have taken me a week to fix.  Now all I have to do is to install transmission that will show in my browser.  I have made any number of runs at that one and failed every time.  I have no idea why this is as I have installed that several times with no problem and its pretty straight forward.  Ubuntu software also has transmission remote but I think its a snap installation and I have not been delighted with snap.

Thanks again!

---

### Post by sudodus on 2021-08-22
Unless quickly solved here I suggest that you create a new thread, that can catch the attention of people who know about transmission. (I use it, but have always been happy with the standard version that ins bundled with Lubuntu). I can see in Ubuntu 20.04.x LTS, that there is a version in the repository universe, that you can insstall via
```

sudo apt update && sudo apt upgrade
sudo apt install transmission

```

If still problems I must ask: Is there a graphical desktop environment or at least some basic x11 server in the remote computer? Transmission has a graphical user interface and would not feel welcome if only text mode.

---

