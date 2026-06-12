---
title: "fstab mistake led to mounting errors"
date: 2016-01-03
forum: General Help
---

### Post by andre46 on 2016-01-03
I dun messed up editing fstab, and now my external drives won't mount correctly. It seems they can still be accessed by Linux through file explorer, however they are no longer accessible through NFS or Samba, which is kind of a big deal for me. I was trying to add some automated bindings for FTP usage, which I apparently did incorrectly.

Here is an example of what I get when trying to unmount my external volumes:

```
Error unmounting /dev/sde1: Command-line `umount  "/media/andre/5TB_1"' exited with non-zero exit status 32: umount: /media/andre/5TB_1: not mounted (udisks-error-quark, 0)
```

Here are the lines that I had added to my fstab file, which was apparently a huge mistake, since I have absolutely no idea what I'm doing:

```
"/media/andre/4TB_1/Movies (New)" /home/andre/FTP-Share/Movies_New        none    bind
"/media/andre/4TB_1/Movies Archive" /home/andre/FTP-Share/Movies_Archive_#-J        none    bind
"/media/andre/4TB_3/Movies Archive (K-Z)" /home/andre/FTP-Share/Movies_Archive_K-Z        none    bind
/media/andre/2TB/Completed/TV/ /home/andre/FTP-Share/TV_New        none    bind
/media/andre/4TB_2/TV_Archive_#-F /home/andre/FTP-Share/TV_Archive_#-F        none    bind
/media/andre/5TB_1/TV_Archive_G-R /home/andre/FTP-Share/TV_Archive_G-R        none    bind
/media/andre/5TB_2/TV_Archive_S-Z /home/andre/FTP-Share/TV_Archive_S-Z        none    bind
"/media/andre/4TB_1/Movies (New)" /home/andre/FTP-ReadOnly/Movies_New        none    bind
"/media/andre/4TB_1/Movies Archive" /home/andre/FTP-ReadOnly/Movies_Archive_#-J        none    bind
"/media/andre/4TB_3/Movies Archive (K-Z)" /home/andre/FTP-ReadOnly/Movies_Archive_K-Z        none    bind
/media/andre/2TB/Completed/TV/ /home/andre/FTP-ReadOnly/TV_New        none    bind
/media/andre/4TB_2/TV_Archive_#-F /home/andre/FTP-ReadOnly/TV_Archive_#-F        none    bind
/media/andre/5TB_1/TV_Archive_G-R /home/andre/FTP-ReadOnly/TV_Archive_G-R        none    bind
/media/andre/5TB_2/TV_Archive_S-Z /home/andre/FTP-ReadOnly/TV_Archive_S-Z        none    bind
/media/andre/2TB/Marcus/ /home/andre/FTP-ReadOnly/Marcus        none    bind
```

I should note that apparently the drives 4TB_1 and 4TB_3 are still accessible for some reason, so it is just 4TB_2, 2TB, 5TB_1 and 5TB_2 that are not appearing. I've removed all the lines I added from fstab, and rebooted, but it is still having the same issue.

---

### Post by Bashing-om on 2016-01-03
andre46;

subscribed :)

Good luck learning NFS bindings .

[indent][indent]together we can
[indent][indent]

---

### Post by andre46 on 2016-01-04
ok, I've got no idea what I'm doing - but I'm trying...

I noticed the error messages I get don't coordinate with which drive I'm trying to unmount.

When I try to unmount the:
2TB_1 drive:
```
Error unmounting /dev/sde1: Command-line `umount  "/media/andre/5TB_1"' exited with non-zero exit status 32: umount: /media/andre/5TB_1: not mounted
```
4TB_1 drive:
```
Error unmounting /dev/sdc1: Command-line `umount  "/media/andre/4TB_1"' exited with non-zero exit status 32: umount: /media/andre/4TB_1: target is busy        (In some cases useful info about processes that
         use the device is found by lsof(8) or fuser(1).)
 (udisks-error-quark, 14)
```
5TB_2: no error
5TB_1:
```
Error unmounting /dev/sdb1: Command-line `umount  "/media/andre/4TB_2"' exited with non-zero exit status 32: umount: /media/andre/4TB_2: not mounted
```
4TB_2: no error
4TB_3:
```
Error unmounting /dev/sdg1: Command-line `umount  "/media/andre/5TB_2"' exited with non-zero exit status 32: umount: /media/andre/5TB_2: not mounted
```

When I tried to manually mount the drives, everything looks fine...
```
andre@NAS:~$ sudo mount -t ext4 /dev/sdg1 /media/andre/4TB_3 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: /dev/sdg1 is already mounted or /media/andre/4TB_3 busy
       /dev/sdg1 is already mounted on /media/andre/4TB_3
andre@NAS:~$ sudo mount -t ext4 /dev/sdd1 /media/andre/5TB_21 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: /dev/sdd1 is already mounted or /media/andre/5TB_21 busy
       /dev/sdd1 is already mounted on /media/andre/5TB_21
andre@NAS:~$ sudo mount -t ext4 /dev/sde1 /media/andre/2TB1 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: /dev/sde1 is already mounted or /media/andre/2TB1 busy
       /dev/sde1 is already mounted on /media/andre/2TB1
andre@NAS:~$ sudo mount -t ext4 /dev/sdc1 /media/andre/4TB_1 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: /dev/sdc1 is already mounted or /media/andre/4TB_1 busy
       /dev/sdc1 is already mounted on /media/andre/4TB_1
andre@NAS:~$ sudo mount -t ext4 /dev/sdb1 /media/andre/5TB_11 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: /dev/sdb1 is already mounted or /media/andre/5TB_11 busy
       /dev/sdb1 is already mounted on /media/andre/5TB_11
andre@NAS:~$ sudo mount -t ext4 /dev/sdf1 /media/andre/4TB_21 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: /dev/sdf1 is already mounted or /media/andre/4TB_21 busy
       /dev/sdf1 is already mounted on /media/andre/4TB_21
```

---

### Post by Bashing-om on 2016-01-04
andre46; Just as a thought.
What returns:
```

sudo mount -a

```
Does the system advise of any errors ?

[INDENT][INDENT]Mind ya, I do not know
[/INDENT][/INDENT]

---

### Post by andre46 on 2016-01-04
I just manually unmounted all the drives with

```
sudo umount -l
```

I ran what you suggested, and got no message.  I then mounted one of the disks again with the Disks app - I still get the same error, and still no message returned from what you suggested :(

I tried to do the entire mounting process manually

```
andre@NAS:~$ sudo umount -l /dev/sdg1
andre@NAS:~$ sudo mkdir /media/andre/4TB_3
andre@NAS:~$ sudo mount -t ext4 /dev/sdg1 /media/andre/4TB_3 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```

This worked for the above drive, but failed for a couple others:
```
andre@NAS:~$ sudo mount -t ext4 /dev/sdb1 /media/andre/5TB_11 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
andre@NAS:~$ sudo mount -t ext4 /dev/sdd1 /media/andre/5TB_21 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```

bump with more info:

I just noticed something about the binds that I had added to fstab... notice how the mount points don't match the physical mount points? Perhaps I entered them wrong... I tried to bind "/media/andre/5TB_1", but apparently the mount point is actually "/media/andre/5TB_11".

I did notice that after unmounting everything, there were still 4 folders in the /media/andre folder... I can't remember what they were at the moment.  Please - I need some guesses here!

---

### Post by matt_symes on 2016-01-05
Hi

I use many bind mounts on my media server.

I can't really make heads nor tails of you fstab file though. Could you please post it again in its entirety.

From ```
man ftsb
```

> If the name of the mount point contains spaces these can be escaped as `\040'.

You want to use \040 instead of spaces in paths in your fstab and remove the quotes. You also still want the dump and fsck fields.

Kind regards

---

### Post by andre46 on 2016-01-05
```
andre@NAS:~$ man ftsb
No manual entry for ftsb
```

```
sudo vi /etc/fstab
```

produces this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
# all my bound mount points
#

```

so prior, the file would have looked like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
# all my bound mount points
#
"/media/andre/4TB_1/Movies (New)" /home/andre/FTP-Share/Movies_New        none    bind
"/media/andre/4TB_1/Movies Archive" /home/andre/FTP-Share/Movies_Archive_#-J        none    bind
"/media/andre/4TB_3/Movies Archive (K-Z)" /home/andre/FTP-Share/Movies_Archive_K-Z        none    bind
/media/andre/2TB/Completed/TV/ /home/andre/FTP-Share/TV_New        none    bind
/media/andre/4TB_2/TV_Archive_#-F /home/andre/FTP-Share/TV_Archive_#-F        none    bind
/media/andre/5TB_1/TV_Archive_G-R /home/andre/FTP-Share/TV_Archive_G-R        none    bind
/media/andre/5TB_2/TV_Archive_S-Z /home/andre/FTP-Share/TV_Archive_S-Z        none    bind
"/media/andre/4TB_1/Movies (New)" /home/andre/FTP-ReadOnly/Movies_New        none    bind
"/media/andre/4TB_1/Movies Archive" /home/andre/FTP-ReadOnly/Movies_Archive_#-J        none    bind
"/media/andre/4TB_3/Movies Archive (K-Z)" /home/andre/FTP-ReadOnly/Movies_Archive_K-Z        none    bind
/media/andre/2TB/Completed/TV/ /home/andre/FTP-ReadOnly/TV_New        none    bind
/media/andre/4TB_2/TV_Archive_#-F /home/andre/FTP-ReadOnly/TV_Archive_#-F        none    bind
/media/andre/5TB_1/TV_Archive_G-R /home/andre/FTP-ReadOnly/TV_Archive_G-R        none    bind
/media/andre/5TB_2/TV_Archive_S-Z /home/andre/FTP-ReadOnly/TV_Archive_S-Z        none    bind
/media/andre/2TB/Marcus/ /home/andre/FTP-ReadOnly/Marcus        none    bind

```

---

### Post by matt_symes on 2016-01-05
Hi

> **andre46 said:**
> ```
andre@NAS:~$ man ftsb
No manual entry for ftsb
```

That was a typo and should have been

```
man fstab
```

but the topic of this thread is about your /etc/fstab file.

Try to power through the odd typo you may see and really try to understand what you are doing.

> **andre46 said:**
> ```
sudo vi /etc/fstab
```

produces this:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
# all my bound mount points
#

```

so prior, the file would have looked like this:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
# all my bound mount points
#
"/media/andre/4TB_1/Movies (New)" /home/andre/FTP-Share/Movies_New        none    bind
"/media/andre/4TB_1/Movies Archive" /home/andre/FTP-Share/Movies_Archive_#-J        none    bind
"/media/andre/4TB_3/Movies Archive (K-Z)" /home/andre/FTP-Share/Movies_Archive_K-Z        none    bind
/media/andre/2TB/Completed/TV/ /home/andre/FTP-Share/TV_New        none    bind
/media/andre/4TB_2/TV_Archive_#-F /home/andre/FTP-Share/TV_Archive_#-F        none    bind
/media/andre/5TB_1/TV_Archive_G-R /home/andre/FTP-Share/TV_Archive_G-R        none    bind
/media/andre/5TB_2/TV_Archive_S-Z /home/andre/FTP-Share/TV_Archive_S-Z        none    bind
"/media/andre/4TB_1/Movies (New)" /home/andre/FTP-ReadOnly/Movies_New        none    bind
"/media/andre/4TB_1/Movies Archive" /home/andre/FTP-ReadOnly/Movies_Archive_#-J        none    bind
"/media/andre/4TB_3/Movies Archive (K-Z)" /home/andre/FTP-ReadOnly/Movies_Archive_K-Z        none    bind
/media/andre/2TB/Completed/TV/ /home/andre/FTP-ReadOnly/TV_New        none    bind
/media/andre/4TB_2/TV_Archive_#-F /home/andre/FTP-ReadOnly/TV_Archive_#-F        none    bind
/media/andre/5TB_1/TV_Archive_G-R /home/andre/FTP-ReadOnly/TV_Archive_G-R        none    bind
/media/andre/5TB_2/TV_Archive_S-Z /home/andre/FTP-ReadOnly/TV_Archive_S-Z        none    bind
/media/andre/2TB/Marcus/ /home/andre/FTP-ReadOnly/Marcus        none    bind

```

Let me give you an example from a fstab file i have. Maybe that will help you.

Below is an entry from a server i own. The first entry is the standard mount and the second is a bind mount that uses a folder that the standard mount exposed.

```
# Mount 2
UUID=b4f3bdae-ad59-433c-ae8f-46b5b1008839 /mnt/storage_2                                ext4 defaults,nobootwait,noatime 0 2 

# Bind mount for pxe
/mnt/storage_2/srv_pxe_isos/tftp                /srv/tftp                               none bind 0 0
```

In the above *b4f3bdae-ad59-433c-ae8f-46b5b1008839* is the UUID of a drive in the sever as shown below.
```

media-server1:/mnt/storage_2/virtual_machines/isos:3 % sudo blkid | grep b4f3
/dev/sdb1: LABEL="2" UUID="b4f3bdae-ad59-433c-ae8f-46b5b1008839" TYPE="ext4" 
media-server1:/mnt/storage_2/virtual_machines/isos:3 %
```

This gets mounted to the location /mnt/storage_2 as shown below.

```

media-server1:/mnt/storage_2/virtual_machines/isos:3 % mountpoint /mnt/storage_2
/mnt/storage_2 is a mountpoint
media-server1:/mnt/storage_2/virtual_machines/isos:3 % 
```

Now for the bind mount, i want to mount the folder [COLOR="#B22222"]/mnt/storage_2/srv_pxe_isos/tftp[/COLOR] so i can see its content at the location [COLOR="#008000"]/srv/tftp[/COLOR].

```
[COLOR="#B22222"]/mnt/storage_2/srv_pxe_isos/tftp[/COLOR]                [COLOR="#008000"]/srv/tftp[/COLOR]                               none bind [COLOR="#0000FF"]0 0[/COLOR]
```

I specify none for the file system and bind as its mount options. I also use [COLOR="#0000FF"]0 0[/COLOR] as the dump and fsck options.

When  they are mounted....

```
sudo mount -a
```

.../srv/tftp is now a mountpoint
```

media-server1:/mnt/storage_2/virtual_machines/isos:3 % mountpoint /srv/tftp
/srv/tftp is a mountpoint
media-server1:/mnt/storage_2/virtual_machines/isos:
```

and the contents of the folder /mnt/storage_2/srv_pxe_isos/tftp are also be viewed at the location /srv/tftp.

Now, my example and walkthrough above contains no spaces. The easiest way to deal with spaces is not to use them in paths. Just rename your paths  to remove spaces and adjust your fstab file accordingly. This is the option i choose.

However, if you must use spaces, then here is an example of how to format them in your fstab using an example you posted.

```
"/media/andre/4TB_1/Movie**s A**rchive"
``` 

in your fstab would be changed

```
/media/andre/4TB_1/Movie**s\040A**rchive
```

So please stop blindly running commands from the Internet without at least some understanding what they are trying to show or tell you.
> 
andre@NAS:~$ man ftsb
No manual entry for ftsb

Kind regards

---

### Post by andre46 on 2016-01-06
Thanks - I'll admit to a blind copypasta, and I'll attribute that to a large amount of trust in a forum moderator.  The spelling was far enough off for me to think it may not be a typo.  As you saw - after I submitted - I realized there was a chance you meant fstab, hence why I sent the follow up message.

Moving forward...

I'd rather not remove the spaces in my paths at this point.  I would need to reconfigure NFS, samba, and the things that point to those paths on the NAS.  However, I did realize that I should have been doing that a couple months back, and I have now gotten into the habit of creating paths without spaces.  So moving forward, I've learned my lesson.

so - I will spend some time making the fstab file - If you don't mind, before I apply it, I'd like to post it here so you can glance it over.  But while I'm working on that, I want to bring this to your attention.  I'm not quite sure what to do with this information:

```

andre@NAS:~$ sudo umount /dev/sdf1
andre@NAS:~$ sudo mkdir /media/andre/4TB_21
andre@NAS:~$ sudo mount -t ext4 /dev/sdf1 /media/andre/4TB_21 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
andre@NAS:~$ sudo umount /dev/sdb1
andre@NAS:~$ sudo mkdir 5TB_11
andre@NAS:~$ sudo mount -t ext4 /dev/sdb1 /media/andre/5TB_11 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```


But some of the drives work fine doing this:
```
andre@NAS:~$ sudo umount /dev/sdg1
andre@NAS:~$ sudo mkdir /media/andre/4TB_3
andre@NAS:~$ sudo mount -t ext4 /dev/sdg1 /media/andre/4TB_3 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```

Ran this:
```

andre@NAS:~$ sudo fdisk -l
[sudo] password for andre: 


Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: ACFD792E-2C80-4140-8521-A86C62920137


Device         Start       End   Sectors  Size Type
/dev/sda1       2048   1050623   1048576  512M Linux filesystem
/dev/sda2    1050624 621787135 620736512  296G Linux filesystem
/dev/sda3  621787136 625141759   3354624  1.6G Linux swap


GPT PMBR size mismatch (3907027053 != 3907027054) will be corrected by w(rite).
The backup GPT table is corrupt, but the primary appears OK, so that will be used.


Disk /dev/sde: 1.8 TiB, 2000397852160 bytes, 3907027055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C38F43A0-9298-46B6-AEC8-4CBC68F59006


Device     Start        End    Sectors  Size Type
/dev/sde1   2048 3907027020 3907024973  1.8T Linux filesystem


Disk /dev/sdc: 3.7 TiB, 4000787025920 bytes, 976754645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 1DE38BF1-3C3F-4818-ADF1-A1BE2576C74B


Device     Start       End   Sectors  Size Type
/dev/sdc1    256 976562755 976562500  3.7T Linux filesystem


Disk /dev/sdd: 4.6 TiB, 5000981073920 bytes, 1220942645 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xd6123fa7


Device     Boot Start        End    Sectors  Size Id Type
/dev/sdd1         256 1220942644 1220942389  4.6T 83 Linux


Disk /dev/sdb: 4.6 TiB, 5000981077504 bytes, 9767541167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C07FE42F-879A-40D9-BF37-69453CA5229B


Device     Start        End    Sectors  Size Type
/dev/sdb1   2048 9767541133 9767539086  4.6T Linux filesystem


Disk /dev/sdh: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 3D607F45-F7CF-41E1-BA63-CAC7D0D3CB77


Device     Start        End    Sectors  Size Type
/dev/sdh1   2048 3907029134 3907027087  1.8T Microsoft basic data


Disk /dev/sdf: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 8B16B774-9FF8-452D-9858-26C6D7D4E5BA


Device     Start        End    Sectors  Size Type
/dev/sdf1   2048 7814037134 7814035087  3.7T Linux filesystem


Disk /dev/sdg: 3.7 TiB, 4000787030016 bytes, 7814037168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 24B31828-EF36-11E3-8493-D067E5F13362


Device     Start        End    Sectors  Size Type
/dev/sdg1   2048 7814037134 7814035087  3.7T Linux filesystem
```

and a few excel functions later, here's what I've got for the fstab file:
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=C38F43A0-9298-46B6-AEC8-4CBC68F59006 /media/andre/2TB1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=1DE38BF1-3C3F-4818-ADF1-A1BE2576C74B /media/andre/4TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=8B16B774-9FF8-452D-9858-26C6D7D4E5BA /media/andre/4TB_21                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=24B31828-EF36-11E3-8493-D067E5F13362 /media/andre/4TB_3                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=C07FE42F-879A-40D9-BF37-69453CA5229B /media/andre/5TB_11                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=0xd6123fa7 /media/andre/5TB_21                                ext4 defaults,nobootwait,noatime 0 2
#
#### BINDS ####
# FTP SHARE FOLDER
/media/andre/4TB_1/Movies\04(New)                /home/andre/FTP-Share/Movies_New                               none bind 0 0
/media/andre/4TB_1/Movies\04Archive                /home/andre/FTP-Share/Movies_Archive_#-J                               none bind 0 0
/media/andre/4TB_3/Movies\04Archive\04(K-Z)                /home/andre/FTP-Share/Movies_Archive_K-Z                               none bind 0 0
/media/andre/2TB/Completed/TV/                /home/andre/FTP-Share/TV_New                               none bind 0 0
/media/andre/4TB_2/TV_Archive_#-F                /home/andre/FTP-Share/TV_Archive_#-F                               none bind 0 0
/media/andre/5TB_1/TV_Archive_G-R                /home/andre/FTP-Share/TV_Archive_G-R                               none bind 0 0
/media/andre/5TB_2/TV_Archive_S-Z                /home/andre/FTP-Share/TV_Archive_S-Z                               none bind 0 0
# FTP READ ONLY FOLDER
/media/andre/4TB_1/Movies\04(New)                /home/andre/FTP-ReadOnly/Movies_New                               none bind 0 0
/media/andre/4TB_1/Movies\04Archive                /home/andre/FTP-ReadOnly/Movies_Archive_#-J                               none bind 0 0
/media/andre/4TB_3/Movies\04Archive\04(K-Z)                /home/andre/FTP-ReadOnly/Movies_Archive_K-Z                               none bind 0 0
/media/andre/2TB/Completed/TV/                /home/andre/FTP-ReadOnly/TV_New                               none bind 0 0
/media/andre/4TB_2/TV_Archive_#-F                /home/andre/FTP-ReadOnly/TV_Archive_#-F                               none bind 0 0
/media/andre/5TB_1/TV_Archive_G-R                /home/andre/FTP-ReadOnly/TV_Archive_G-R                               none bind 0 0
/media/andre/5TB_2/TV_Archive_S-Z                /home/andre/FTP-ReadOnly/TV_Archive_S-Z                               none bind 0 0
/media/andre/2TB/Marcus/                /home/andre/FTP-ReadOnly/Marcus                               none bind 0 0
```

---

### Post by matt_symes on 2016-01-06
Hi

> Thanks - I'll admit to a blind copypasta, and I'll attribute that to a large amount of trust in a forum moderator. The spelling was far enough off for me to think it may not be a typo. As you saw - after I submitted - I realized there was a chance you meant fstab, hence why I sent the follow up message.

This is fair enough and my post may have come across more terse than i intended it to come across.

Anyway...

The last part of your second post should be quicker to address as the first post and the first part of the second post look more serious so I'll put them in another post.

> ```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=C38F43A0-9298-46B6-AEC8-4CBC68F59006 /media/andre/2TB1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=1DE38BF1-3C3F-4818-ADF1-A1BE2576C74B /media/andre/4TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=8B16B774-9FF8-452D-9858-26C6D7D4E5BA /media/andre/4TB_21                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=24B31828-EF36-11E3-8493-D067E5F13362 /media/andre/4TB_3                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=C07FE42F-879A-40D9-BF37-69453CA5229B /media/andre/5TB_11                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=0xd6123fa7 /media/andre/5TB_21                                ext4 defaults,nobootwait,noatime 0 2
#
#### BINDS ####
# FTP SHARE FOLDER
[B]/media/andre/4TB_1/Movies\04(New)                /home/andre/FTP-Share/Movies_New                               none bind 0 0
/media/andre/4TB_1/Movies\04Archive                /home/andre/FTP-Share/Movies_Archive_#-J                               none bind 0 0
/media/andre/4TB_3/Movies\04Archive\04(K-Z)                /home/andre/FTP-Share/Movies_Archive_K-Z                               none bind 0 0[/B]
/media/andre/2TB/Completed/TV/                /home/andre/FTP-Share/TV_New                               none bind 0 0
/media/andre/4TB_2/TV_Archive_#-F                /home/andre/FTP-Share/TV_Archive_#-F                               none bind 0 0
/media/andre/5TB_1/TV_Archive_G-R                /home/andre/FTP-Share/TV_Archive_G-R                               none bind 0 0
/media/andre/5TB_2/TV_Archive_S-Z                /home/andre/FTP-Share/TV_Archive_S-Z                               none bind 0 0
# FTP READ ONLY FOLDER
/media/andre/4TB_1/Movies\04(New)                /home/andre/FTP-ReadOnly/Movies_New                               none bind 0 0
/media/andre/4TB_1/Movies\04Archive                /home/andre/FTP-ReadOnly/Movies_Archive_#-J                               none bind 0 0
/media/andre/4TB_3/Movies\04Archive\04(K-Z)                /home/andre/FTP-ReadOnly/Movies_Archive_K-Z                               none bind 0 0
/media/andre/2TB/Completed/TV/                /home/andre/FTP-ReadOnly/TV_New                               none bind 0 0
/media/andre/4TB_2/TV_Archive_#-F                /home/andre/FTP-ReadOnly/TV_Archive_#-F                               none bind 0 0
/media/andre/5TB_1/TV_Archive_G-R                /home/andre/FTP-ReadOnly/TV_Archive_G-R                               none bind 0 0
/media/andre/5TB_2/TV_Archive_S-Z                /home/andre/FTP-ReadOnly/TV_Archive_S-Z                               none bind 0 0
/media/andre/2TB/Marcus/                /home/andre/FTP-ReadOnly/Marcus                               none bind 0 0
```

This is almost correct. I've highlighted the problems in bold above and below is how you need to adjust them.

```

# FTP SHARE FOLDER
/media/andre/4TB_1/Movies**\040**(New)                /home/andre/FTP-Share/Movies_New                               none bind 0 0
/media/andre/4TB_1/Movies**\040**Archive                /home/andre/FTP-Share/Movies_Archive_#-J                               none bind 0 0
/media/andre/4TB_3/Movies**\040**Archive**\040**(K-Z)                /home/andre/FTP-Share/Movies_Archive_K-Z                               none bind 0 0

# FTP READ ONLY FOLDER
/media/andre/4TB_1/Movies**\040**(New)                /home/andre/FTP-ReadOnly/Movies_New                               none bind 0 0
/media/andre/4TB_1/Movies**\040**Archive                /home/andre/FTP-ReadOnly/Movies_Archive_#-J                               none bind 0 0
/media/andre/4TB_3/Movies**\040**Archive**\040**(K-Z)                /home/andre/FTP-ReadOnly/Movies_Archive_K-Z                               none bind 0 0
```

The reason is that **\040** is the octal representation of the space character and this is what the fstab file accepts.

I'll take a look at the other parts of your two posts next. You may have a bigger problem there.

Kind regads

---

### Post by matt_symes on 2016-01-06
Hi

> **andre46 said:**
> 
```

andre@NAS:~$ sudo umount /dev/sdf1
andre@NAS:~$ sudo mkdir /media/andre/4TB_21
andre@NAS:~$ sudo mount -t ext4 /dev/sdf1 /media/andre/4TB_21 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
andre@NAS:~$ sudo umount /dev/sdb1
andre@NAS:~$ sudo mkdir 5TB_11
andre@NAS:~$ sudo mount -t ext4 /dev/sdb1 /media/andre/5TB_11 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error


       In some cases useful info is found in syslog - try
       dmesg | tail or so.
```


I would start by running fsck on this drive.

As you cannot mount this drive just boot into your installation as normal, open a terminal and type

```
sudo fsck -yNf /dev/sdb1 
```

That's a capital N above and will run a *simulated* pass of fsck on the drive so it will not actually fix anything.

Post the output from the terminal into your next and and then we can decide what to attempt to fix the partition.

> **andre46 said:**
> Ran this:
```

andre@NAS:~$ sudo fdisk -l
[sudo] password for andre: 

...

GPT PMBR size mismatch (3907027053 != 3907027054) will be corrected by w(rite).
The backup GPT table is corrupt, but the primary appears OK, so that will be used.

Disk /dev/sde: 1.8 TiB, 2000397852160 bytes, 3907027055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: C38F43A0-9298-46B6-AEC8-4CBC68F59006

Device     Start        End    Sectors  Size Type
/dev/sde1   2048 3907027020 3907024973  1.8T Linux filesystem

...



The error message pretty much say's it all, you have a corrupted backup gpt table on /dev/sde. Luckily your primary one at the start of the drive is good.

So we can verify what the problem is, before we attempt to fix it, open a terminal and run the command below. It should give more detail about what is wrong. Please post its output back here and then we can look at a fix.

[CODE]sudo sgdisk -v /dev/sde
```

**EDIT:**

I would also run a smart test on each drive and see what the drives report. It's in no way a solid test but it can be indicative of problems.

If you're not sure how to run a smart test then mention it in your next post and I'll talk you through it. 

Kind regards

---

### Post by Morbius1 on 2016-01-07
Just a side note:
> andre@NAS:~$ sudo mount -t ext4 /dev/sdf1 /media/andre/4TB_21 -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
mount: wrong fs type, bad option, bad superblock on /dev/sdf1,
       missing codepage or helper program, or other error

One of two things is wrong with that mount statement:

*** You can't use "uid=1000,gid=1000,utf8,dmask=027,fmask=137" options on an ext4 partition.
*** OR, It's not an ext4 partition but an NTFS partition in which case the "uid=1000,gid=1000,utf8,dmask=027,fmask=137" options can be used.

So either:

** Change the fs type from ext4 to ntfs if the partition is ntfs.
** Or remove the "uid=1000,gid=1000,utf8,dmask=027,fmask=137" options string and replace it with defaults.

---

### Post by matt_symes on 2016-01-07
Hi

> **Morbius1 said:**
> Just a side note:


One of two things is wrong with that mount statement:

*** You can't use "uid=1000,gid=1000,utf8,dmask=027,fmask=137" options on an ext4 partition.
*** OR, It's not an ext4 partition but an NTFS partition in which case the "uid=1000,gid=1000,utf8,dmask=027,fmask=137" options can be used.

So either:

** Change the fs type from ext4 to ntfs if the partition is ntfs.
** Or remove the "uid=1000,gid=1000,utf8,dmask=027,fmask=137" options string and replace it with defaults.

An excellent point and I'm glad you mentioned it.

If you have any basic/clear but useful fstab and mounting links for the OP then please post them as they'll be useful for the OP.l as I'm not sure what time I'll be nearer anything larger than this phone.

Kind regards

---

### Post by andre46 on 2016-01-07
ok - lots going on here.

First of all - great catch with the missing character in the fstab lines.  I've updated that.

I ran that fsck command on both of the drives I posted that error for

```

andre@NAS:~$ sudo fsck -yNf /dev/sdb1
fsck from util-linux 2.25.2
[/sbin/fsck.ext4 (1) -- /dev/sdb1] fsck.ext4 -yf /dev/sdb1 
andre@NAS:~$ sudo fsck -yNf /dev/sdf1
fsck from util-linux 2.25.2
[/sbin/fsck.ext4 (1) -- /dev/sdf1] fsck.ext4 -yf /dev/sdf1

```

No idea what that means.  Hopefully it's not terrible.

I apparently didn't have gdisk installed, so I've installed it:

```

andre@NAS:~$ sudo sgdisk -v /dev/sde
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.


****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************


Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.


Identified 1 problems!

```

I can see how to run the SMART self-test through the DISKS app.  Looks like the drive needs to be unmounted?  I'm not sure if there is a command line way that you feel is better.

Sounds like it's time to mention something I didn't think was important, and you're probably going to be mad.  I was certain this was all caused by the fstab file, but I had a power outage, which is why my server rebooted in the first place.  Between the power strip and the battery backup, nothing should have been fried.  At no point did I think this was a hardware issue until just before my last response.


Thanks for your comment, Morbius.  I'll be sure to either stop manually mounting these (since the DISKS app can mount just fine), or eliminate those options from future manual mounts.

Side note - all but one of the drives connected to this server are EXT4.  There is a single NTFS drive, but I have nothing of value on it, and intend to format to EXT4 at some point.  That drive has not been mentioned in this thread at all.

---

### Post by matt_symes on 2016-01-08
Hi

> **andre46 said:**
> ok - lots going on here.

First of all - great catch with the missing character in the fstab lines.  I've updated that.

I ran that fsck command on both of the drives I posted that error for

```

andre@NAS:~$ sudo fsck -yNf /dev/sdb1
fsck from util-linux 2.25.2
[/sbin/fsck.ext4 (1) -- /dev/sdb1] fsck.ext4 -yf /dev/sdb1 
andre@NAS:~$ sudo fsck -yNf /dev/sdf1
fsck from util-linux 2.25.2
[/sbin/fsck.ext4 (1) -- /dev/sdf1] fsck.ext4 -yf /dev/sdf1

```

No idea what that means.  Hopefully it's not terrible.


That looks fine. 

I wanted you run run fsck on the partition to ensure there were no errors on it. You had those errors, though, because you were passing in the options that Mobius point out, into the mount command and not due to filesystem corruption on the partition.

BTW: I fat fingered sdb1, which should have been sdf1, so thanks for running fsck on the correct partition.

> I apparently didn't have gdisk installed, so I've installed it:

```

andre@NAS:~$ sudo sgdisk -v /dev/sde
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.


****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************


Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.


Identified 1 problems!

```


This is a problem though.

First make a backup of the partition table of /dev/sde to a file in your home directory.

```
sudo sgdisk -b ~/partition-table.bk /dev/sde
```

Now let's try to fix the drive. We have to use gdisk *(not sgdisk this time)* in recovery mode.

```
sudo gdisk /dev/sde
```

You will see this
```

....
....
Command (? for help):

```

Press w to write and q to exit.

Then verify the drive again with

```
sudo sgdisk -v /dev/sde
```

Post back the output from the last command.

> I can see how to run the SMART self-test through the DISKS app.  Looks like the drive needs to be unmounted?  I'm not sure if there is a command line way that you feel is better.

Sounds like it's time to mention something I didn't think was important, and you're probably going to be mad.  I was certain this was all caused by the fstab file, but I had a power outage, which is why my server rebooted in the first place.  Between the power strip and the battery backup, nothing should have been fried.  At no point did I think this was a hardware issue until just before my last response.


You can run a smart test on drives that are both mounted and unmounted. It makes no difference.

You can use the disks utility to do it. I generally use the command line, using smartctl, but if you have a GUI on this PC then it really makes no difference. 

> Thanks for your comment, Morbius.  I'll be sure to either stop manually mounting these (since the DISKS app can mount just fine), or eliminate those options from future manual mounts.

Side note - all but one of the drives connected to this server are EXT4.  There is a single NTFS drive, but I have nothing of value on it, and intend to format to EXT4 at some point.  That drive has not been mentioned in this thread at all.

We're getting there :)

Kind regards

---

### Post by andre46 on 2016-01-08
ok, I'm one button click away, but I'm afraid this is going to destroy the data on my disk.  Is that correct?  Should I backup this drive first?

```

andre@NAS:~$ sudo gdisk /dev/sde
GPT fdisk (gdisk) version 0.8.10


Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.


Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged


****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************


Command (? for help): w
Warning! Secondary header is placed too early on the disk! Do you want to
correct this problem? (Y/N): y
Have moved second header and partition table to correct location.


Final checks complete. About to write GPT data. THIS WILL OVERWRITE EXISTING
PARTITIONS!!


Do you want to proceed? (Y/N): 

```

---

### Post by matt_symes on 2016-01-08
Hi

Sorry for the delay. I've been AFK. 

Go for it. It looks good and you have a backup of the partition table if there are problems.

EDIT:

Just noticed you posted 3 minutes before me so that was good timing :)

Kind regards

---

### Post by andre46 on 2016-01-08
```

andre@NAS:~$ sudo sgdisk -v /dev/sde
[sudo] password for andre: 


No problems found. 2015 free sectors (1007.5 KiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

```

The SMART tests may have to wait until the end of the weekend

---

### Post by matt_symes on 2016-01-08
Hi

> **andre46 said:**
> ```

andre@NAS:~$ sudo sgdisk -v /dev/sde
[sudo] password for andre: 


No problems found. 2015 free sectors (1007.5 KiB) available in 2
segments, the largest of which is 2014 (1007.0 KiB) in size.

```

The SMART tests may have to wait until the end of the weekend

That looks fine. Are all your partitions mounting now ?

You may want to post the output of the command below after a reboot

```
mount | grep ^/
```

Kind regards

---

### Post by andre46 on 2016-01-08
Ok,
```

andre@NAS:~$ mount | grep ^/
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdh1 on /media/andre/2TB1 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdg1 on /media/andre/4TB_1 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sde1 on /media/andre/5TB_12 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1 on /media/andre/4TB_22 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
```

But please take a look at [this screenshot]("http://imgur.com/3d1kLaq") regarding the 2TB_1 drive.  Notice that folders don't seem to jibe between the reports.

Also, [why are there so many folders in the /media/andre/ folder]("http://imgur.com/XXaAxQY")??

I still can't easily unmount all of the drives, and when I try to access the server via samba:
1 drive is accessible without issue (4TB_1)
1 drive opens to an empty folder (4TB_3)
The other 4 drives don't let me connect, saying the credentials are incorrect.

It looks like all of the drives did a SMART self test after the reboot, and everything looks fine...

wow - I literally just realized that nothing is showing up in samba because all the samba shares are mapped to the /media/andre folder, and it seems each of the drives keeps mounting to different places whenever I reboot.

So... next steps... unmount all the drives, delete all the folders within /media/andre/ and then mount them again...?

---

### Post by matt_symes on 2016-01-09
Hi

> **andre46 said:**
> Ok,
```

andre@NAS:~$ mount | grep ^/
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdh1 on /media/andre/2TB1 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdg1 on /media/andre/4TB_1 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sde1 on /media/andre/5TB_12 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1 on /media/andre/4TB_22 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
```

But please take a look at [this screenshot]("http://imgur.com/3d1kLaq") regarding the 2TB_1 drive.  Notice that folders don't seem to jibe between the reports.

Also, [why are there so many folders in the /media/andre/ folder]("http://imgur.com/XXaAxQY")??

I still can't easily unmount all of the drives, and when I try to access the server via samba:
1 drive is accessible without issue (4TB_1)
1 drive opens to an empty folder (4TB_3)
The other 4 drives don't let me connect, saying the credentials are incorrect.

It looks like all of the drives did a SMART self test after the reboot, and everything looks fine...

Are your drives external USB drives ? 

> ,uhelper=udisks2)

udisks is mounting them and not your fstab file. You want either the fstab file or udisks to mount them.

> **andre46 said:**
> wow - I literally just realized that nothing is showing up in samba because all the samba shares are mapped to the /media/andre folder, and it seems each of the drives keeps mounting to different places whenever I reboot.

So... next steps... unmount all the drives, delete all the folders within /media/andre/ and then mount them again...?

Let's back up a bit and start from the beginning. Forget about samba and nfs for the moment.

Are your drives USB ?

Kind regards

---

### Post by andre46 on 2016-01-09
I'm not home at the moment, but I'm pretty sure I figured out the issue.

First of all - my fstab file is still blank, so fstab is not doing any of the mounting.  And yes, all the drives are USB

I think my initial fstab edit caused 4 of the folders mounted in /media/andre/ (the 4 that DIDN'T have any quotes around them) to change the filesystem of the folder (due to the options that Morbius had mentioned).  When I rebooted, ubuntu couldn't mount the drive to that folder because the filesystem of the drive didn't match that of the folder, so it created a new folder with a "1" appended to the end.  This is why the drives aren't showing up in samba or nfs - because, for example, /media/andre/2TB is now mounting to /media/andre/2TB1.  Then I manually unmounted all those drives, and then mounted them again manually - but again, I did it with the wrong options, so there was a mismatch in options, so again after the reboot - more folders appearing in the /media/andre/ folder.

This explains why there is a:
/media/andre/4TB_2
/media/andre/4TB_21
/media/andre/4TB_22

So I truly believe that if I unmount all the drives, delete the extra folders from /media/andre/, and then edit the fstab file as we described - I think we'll be in a better position.  Make sense?

---

### Post by matt_symes on 2016-01-09
Hi


> **andre46 said:**
> I'm not home at the moment, but I'm pretty sure I figured out the issue.

First of all - my fstab file is still blank, so fstab is not doing any of the mounting.  And yes, all the drives are USB


That explains why udisks is mounting them and not mountall using your fstab file.

> I think my initial fstab edit caused 4 of the folders mounted in /media/andre/ (the 4 that DIDN'T have any quotes around them) to change the filesystem of the folder (due to the options that Morbius had mentioned).  When I rebooted, ubuntu couldn't mount the drive to that folder because the filesystem of the drive didn't match that of the folder, so it created a new folder with a "1" appended to the end.  This is why the drives aren't showing up in samba or nfs - because, for example, /media/andre/2TB is now mounting to /media/andre/2TB1.  Then I manually unmounted all those drives, and then mounted them again manually - but again, I did it with the wrong options, so there was a mismatch in options, so again after the reboot - more folders appearing in the /media/andre/ folder.


udisks has been mounting your USB drives.

When udisks mounts your USB drives, it will create directories in /media and mount them on those directories.

When using a fstab file, the usual place to create directories to mount drives is not in /media but in /mnt.

/media is usually left alone for udisks to handle while /mnt is usually used to mount drives that are defined in your fstab file.

If you create directories in /media with the same name that udisks would normally create when it mounts drives for you, then udisks will change the name it was going to use for the directory slightly.

This is the reason, i believe, you are getting the extra directories appearing in /media.

It does explain why nfs and samba weren't showing any files though, as udisks had created new directories (different from the ones samba and nfs were configured to share) and mounted the USB drives there.

> This explains why there is a:
/media/andre/4TB_2
/media/andre/4TB_21
/media/andre/4TB_22

So I truly believe that if I unmount all the drives, delete the extra folders from /media/andre/, and then edit the fstab file as we described - I think we'll be in a better position.  Make sense?

I am going to be online tomorrow night. 

If you want to fix these issues and can be at your PC for a number of hours uninterrupted tomorrow then we'll get your system up and running correctly.

I'll make a post and then you can respond and we can keep going like that. Refresh your browser every 10 minutes to check for my reply and i'll do the same my end.

That way we can finish off your system totally tomorrow.

I will be available to help you from 6pm UTC and i can keep going until around 2am UTC. 

Can you make a window of uninterrupted PC time to get your system fixed during that 8 hour time span ? 

If you can then tell me what time (in UTC) you'll be online and how long you can be online for.

Kind regards

---

### Post by andre46 on 2016-01-10
Ok, thanks so much.  I'll be home at about 9pm UTC, and can be online for up to 6 hours or so.

A bit late, but I'm here.  Where do we start?

---

### Post by matt_symes on 2016-01-10
Hi

First i think we should sort out your fstab file and get your drives mounting when you boot up.

I suggest that, instead of mounting them under /media, they get mounted under /mnt.

/mnt is a better place for them.

It does mean we'll have to adjust your samba and nfs configuration but when can do that as well.

Are you happy with this ?

If so then i have a couple of questions.

Does your server have a GUI or is it command line driven ?

Can you post the output of this command

```
cat /etc/lsb-release 
```

After you post the answer to these questions my next post will be some commands for you to run and a modified fstab file for you.

Kind regards

---

### Post by andre46 on 2016-01-10
Well, I'd rather not change the samba and nfs files, but that'll be fine.

My server has a gui.

so with the previous changes, here is what I'm going to copy/paste into my fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=C38F43A0-9298-46B6-AEC8-4CBC68F59006 /mnt/2TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=1DE38BF1-3C3F-4818-ADF1-A1BE2576C74B /mnt/4TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=8B16B774-9FF8-452D-9858-26C6D7D4E5BA /mnt/4TB_2                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=24B31828-EF36-11E3-8493-D067E5F13362 /mnt/4TB_3                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=C07FE42F-879A-40D9-BF37-69453CA5229B /mnt/5TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=0xd6123fa7 /mnt/5TB_2                                ext4 defaults,nobootwait,noatime 0 2
#
#### BINDS ####
# FTP SHARE FOLDER
/mnt/4TB_1/Movies\040(New)                /home/andre/FTP-Share/Movies_New                               none bind 0 0
/mnt/4TB_1/Movies\040Archive                /home/andre/FTP-Share/Movies_Archive_#-J                               none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)                /home/andre/FTP-Share/Movies_Archive_K-Z                               none bind 0 0
/mnt/2TB_1/Completed/TV/                /home/andre/FTP-Share/TV_New                               none bind 0 0
/mnt/4TB_2/TV_Archive_#-F                /home/andre/FTP-Share/TV_Archive_#-F                               none bind 0 0
/mnt/5TB_1/TV_Archive_G-R                /home/andre/FTP-Share/TV_Archive_G-R                               none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z                /home/andre/FTP-Share/TV_Archive_S-Z                               none bind 0 0
# FTP READ ONLY FOLDER
/mnt/4TB_1/Movies\004(New)                /home/andre/FTP-ReadOnly/Movies_New                               none bind 0 0
/mnt/4TB_1/Movies\040Archive                /home/andre/FTP-ReadOnly/Movies_Archive_#-J                               none bind 0 0
/mnt/4TB_3/Movies\040Archive\04(K-Z)                /home/andre/FTP-ReadOnly/Movies_Archive_K-Z                               none bind 0 0
/mnt/2TB_1/Completed/TV/                /home/andre/FTP-ReadOnly/TV_New                               none bind 0 0
/mnt/4TB_2/TV_Archive_#-F                /home/andre/FTP-ReadOnly/TV_Archive_#-F                               none bind 0 0
/mnt/5TB_1/TV_Archive_G-R                /home/andre/FTP-ReadOnly/TV_Archive_G-R                               none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z                /home/andre/FTP-ReadOnly/TV_Archive_S-Z                               none bind 0 0
/mnt/2TB_1/Marcus/                /home/andre/FTP-ReadOnly/Marcus                               none bind 0 0
```

Whoops - I ran your command, but forgot to paste it:
```

andre@NAS:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.04
DISTRIB_CODENAME=vivid
DISTRIB_DESCRIPTION="Ubuntu 15.04"

```

---

### Post by matt_symes on 2016-01-10
Hi

Your fstab file looks good.

You need to create the directories under /mnt.  

If you have not created them then open a terminal and copy and paste this into it.

```
sudo mkdir -p /mnt/{2TB_1,4TB_1,4TB_2,4TB_3,5TB_1,5TB_2}
```

You also want to be the owner of these directories.

```
sudo chown $USER:$USER /mnt/{2TB_1,4TB_1,4TB_2,4TB_3,5TB_1,5TB_2}
```

If you have not already done so then create the FTP folders under your home directory.

```
mkdir -p ~/{FTP-Share,FTP-ReadOnly{,/Marcus}}/{Movies_New,Movies_Archive_#-J,Movies_Archive_K-Z,TV_New,TV_Archive_#-F,TV_Archive_G-R,TV_Archive_S-Z}
```

At this point you should have all the directories set up for you.

Replace the existing contents of your /etc/fstab file with the contents in your previous post. 

You then need to reboot your PC

```
sudo reboot
```

Finally, so we can see where you are, please post the outputs of these commands.

```
mount | egrep "^/|bind"
```

```
ls -l /mnt
```

If your disc are still being mounted under /media then we will need to disable auto-mounting by udisks.

Kind regards

---

### Post by andre46 on 2016-01-10
Big problem - it won't boot again (Bashing-om helped me with this prior, and all was good)

I ran some updates over the past couple days, but nothing errored out.  Otherwise, I haven't touched the thing.

I'm not getting the splash screen - after the BIOS screen, i get grub, and then just a black screen.  I disconnected all drives, and did a hard reboot, and I still can't get back to the gui.

---

### Post by matt_symes on 2016-01-10
Hi

> **andre46 said:**
> Big problem - it won't boot again (Bashing-om helped me with this prior, and all was good)

I ran some updates over the past couple days, but nothing errored out.  Otherwise, I haven't touched the thing.

I'm not getting the splash screen - after the BIOS screen, i get grub, and then just a black screen.  I disconnected all drives, and did a hard reboot, and I still can't get back to the gui.

Wow ! Well, editing you fstab file will not have caused that !

Did bashing-om suggest you use the *nomodeset* kernel parameter to boot to the GUI ?

Kind regards

---

### Post by andre46 on 2016-01-10
no, I've never heard of that.  I've rebooted several times without issue since I worked with him.

Here was the previous thread: [http://ubuntuforums.org/showthread.php?t=2306009](http://ubuntuforums.org/showthread.php?t=2306009)

A lot of what we did was related to kernel issues...?  And I believe there were kernel updates installed in my recent set of updates.

---

### Post by matt_symes on 2016-01-10
Hi

> **andre46 said:**
> no, I've never heard of that.  I've rebooted several times without issue since I worked with him.

Here was the previous thread: [http://ubuntuforums.org/showthread.php?t=2306009](http://ubuntuforums.org/showthread.php?t=2306009)

A lot of what we did was related to kernel issues...?  And I believe there were kernel updates installed in my recent set of updates.

Can you boot into an older kernel from the grub menu ?

Kind regards

---

### Post by andre46 on 2016-01-10
Ok - that worked.  Lets press on, and I'll deal with that later.

However, all the drives are still mounted to /media/andre/

```

andre@NAS:~$ mount | egrep "^/|bind"
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdh1 on /media/andre/2TB1 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdg1 on /media/andre/5TB_22 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdf1 on /media/andre/4TB_1 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sde1 on /media/andre/5TB_12 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdd1 on /media/andre/Transfer Drive type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,default_permissions,allow_other,blksize=4096,uhelper=udisks2)
/dev/sdc1 on /media/andre/4TB_31 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
/dev/sdb1 on /media/andre/4TB_22 type ext4 (rw,nosuid,nodev,relatime,data=ordered,uhelper=udisks2)
andre@NAS:~$ ls -l /mnt
total 24
drwxr-xr-x 2 andre andre 4096 Jan 10 17:09 2TB_1
drwxr-xr-x 2 andre andre 4096 Jan 10 17:09 4TB_1
drwxr-xr-x 2 andre andre 4096 Jan 10 17:09 4TB_2
drwxr-xr-x 2 andre andre 4096 Jan 10 17:09 4TB_3
drwxr-xr-x 2 andre andre 4096 Jan 10 17:09 5TB_1
drwxr-xr-x 2 andre andre 4096 Jan 10 17:09 5TB_2
```

---

### Post by matt_symes on 2016-01-10
Hi

That's odd as it looks to be completely ignoring your fstab file. It's not mounted any of the bind mounts either.

Can we check some things.

Please post the output of 

```
sudo blkid
```

Let's double check your new fstab file.

```
cat /etc/fstab
```

Then let's unmount the drives and try remounting them manually.

```
sudo umount /media/andre/{2TB1,5TB_22,4TB_1,5TB_12,4TB_31,4TB_22}
```

```
sudo mount -a
```

And then if you could post the output of this command again.

```
mount | grep "^/|bind"
```

Kind regards

---

### Post by andre46 on 2016-01-10
Ok - after some work here, I found all the errors in the fstab file (apparently I had the wrong UUIDs???), and there were a few others. Anyway, we're in much better shape now:

```

andre@NAS:~$ sudo blkid
/dev/sda1: UUID="51AB-2663" TYPE="vfat" PARTUUID="c712dc64-a7d7-4ad3-a5dc-e07490a705d3"
/dev/sda2: UUID="e1abd730-7d20-4120-90d2-d71282a96d87" TYPE="ext4" PARTUUID="50cfa454-3cf7-4182-a210-e2fe1882ba4f"
/dev/sda3: UUID="412337ba-019b-45a7-8376-2a9236201a2e" TYPE="swap" PARTUUID="6385f4ee-8cd8-4540-9fb7-62587471f4d4"
/dev/sdb1: LABEL="4TB_2" UUID="affca0f6-7ae8-45f5-9e59-92170c3c437a" TYPE="ext4" PARTUUID="7ed95559-df56-4ae3-84b3-ffb9f98a4db0"
/dev/sdc1: LABEL="4TB_3" UUID="3b7c225a-2602-4224-8a80-dc59d13cc1a4" TYPE="ext4" PARTUUID="d2a98f7e-1857-474b-9973-b2676d2302f0"
/dev/sdd1: LABEL="Transfer Drive" UUID="40CCDE59CCDE4934" TYPE="ntfs" PARTLABEL="Microsoft Basic Data" PARTUUID="702e683a-15a1-4e4c-9210-d28bdbaac88f"
/dev/sde1: LABEL="5TB_1" UUID="c9fd552c-921c-4ddb-bb46-fe557943d311" TYPE="ext4" PARTUUID="3bed9e0c-b45e-4518-9af5-eadcd3a97cc1"
/dev/sdf1: LABEL="4TB_1" UUID="f90279d3-7127-4fdb-845c-7c7f60fd6eec" TYPE="ext4" PARTUUID="4a9a71ca-7c1e-42a0-865e-199de4f8b47c"
/dev/sdg1: LABEL="5TB_2" UUID="2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d" TYPE="ext4"
/dev/sdh1: LABEL="2TB" UUID="f238352a-805e-40e8-a676-c62f0b6b0acb" TYPE="ext4" PARTUUID="5b349937-b657-4c5a-a4e1-1f8eaad3382c"
andre@NAS:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=e1abd730-7d20-4120-90d2-d71282a96d87 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=51AB-2663  /boot/efi       vfat    defaults        0       1
# swap was on /dev/sda3 during installation
UUID=412337ba-019b-45a7-8376-2a9236201a2e none            swap    sw              0       0
#
#
#
#### MOUNT POINTS ####
# 2TB_1
UUID=f238352a-805e-40e8-a676-c62f0b6b0acb /mnt/2TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 2TB_2
#UUID=f238352a-805e-40e8-a676-c62f0b6b0acb /mnt/2TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_1
UUID=f90279d3-7127-4fdb-845c-7c7f60fd6eec /mnt/4TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_2
UUID=affca0f6-7ae8-45f5-9e59-92170c3c437a /mnt/4TB_2                                ext4 defaults,nobootwait,noatime 0 2
# 4TB_3
UUID=3b7c225a-2602-4224-8a80-dc59d13cc1a4 /mnt/4TB_3                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_1
UUID=c9fd552c-921c-4ddb-bb46-fe557943d311 /mnt/5TB_1                                ext4 defaults,nobootwait,noatime 0 2
# 5TB_2
UUID=2b1fcea7-8183-43d4-8a1a-43c54d9e8e5d /mnt/5TB_2                                ext4 defaults,nobootwait,noatime 0 2
#
#### BINDS ####
# FTP SHARE FOLDER
/mnt/4TB_1/Movies\040(New)                /home/andre/FTP-Share/Movies_New                               none bind 0 0
/mnt/4TB_1/Movies\040Archive                /home/andre/FTP-Share/Movies_Archive_#-J                               none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)                /home/andre/FTP-Share/Movies_Archive_K-Z                               none bind 0 0
/mnt/2TB_1/Completed/TV/                /home/andre/FTP-Share/TV_New                               none bind 0 0
/mnt/4TB_2/TV_Archive_#-F                /home/andre/FTP-Share/TV_Archive_#-F                               none bind 0 0
/mnt/5TB_1/TV_Archive_G-R                /home/andre/FTP-Share/TV_Archive_G-R                               none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z                /home/andre/FTP-Share/TV_Archive_S-Z                               none bind 0 0
# FTP READ ONLY FOLDER
/mnt/4TB_1/Movies\040(New)                /home/andre/FTP-ReadOnly/Movies_New                               none bind 0 0
/mnt/4TB_1/Movies\040Archive                /home/andre/FTP-ReadOnly/Movies_Archive_#-J                               none bind 0 0
/mnt/4TB_3/Movies\040Archive\040(K-Z)                /home/andre/FTP-ReadOnly/Movies_Archive_K-Z                               none bind 0 0
/mnt/2TB_1/Completed/TV/                /home/andre/FTP-ReadOnly/TV_New                               none bind 0 0
/mnt/4TB_2/TV_Archive_#-F                /home/andre/FTP-ReadOnly/TV_Archive_#-F                               none bind 0 0
/mnt/5TB_1/TV_Archive_G-R                /home/andre/FTP-ReadOnly/TV_Archive_G-R                               none bind 0 0
/mnt/5TB_2/TV_Archive_S-Z                /home/andre/FTP-ReadOnly/TV_Archive_S-Z                               none bind 0 0
/mnt/2TB_1/Marcus/                /home/andre/FTP-ReadOnly/Marcus                               none bind 0 0
andre@NAS:~$ mount | grep "^/|bind"
andre@NAS:~$ 

```

---

### Post by matt_symes on 2016-01-10
Hi

We just need to check your mounts. There was a typo in my last command. 

Could you post the output of this command

```
mount | egrep "^/|mount"
```

Kind regards

---

### Post by andre46 on 2016-01-10
```

andre@NAS:~$ mount | egrep "^/|mount"
/dev/sda2 on / type ext4 (rw,relatime,errors=remount-ro,data=ordered)
/dev/sda1 on /boot/efi type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/sdh1 on /mnt/2TB_1 type ext4 (rw,noatime,data=ordered)
/dev/sdh1 on /home/andre/FTP-Share/TV_New type ext4 (rw,noatime,data=ordered)
/dev/sdh1 on /home/andre/FTP-ReadOnly/TV_New type ext4 (rw,noatime,data=ordered)
/dev/sdh1 on /home/andre/FTP-ReadOnly/Marcus type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /mnt/4TB_1 type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-Share/Movies_New type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-Share/Movies_Archive_#-J type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-ReadOnly/Movies_Archive_#-J type ext4 (rw,noatime,data=ordered)
/dev/sdc1 on /mnt/4TB_3 type ext4 (rw,noatime,data=ordered)
/dev/sdc1 on /home/andre/FTP-Share/Movies_Archive_K-Z type ext4 (rw,noatime,data=ordered)
/dev/sde1 on /mnt/5TB_1 type ext4 (rw,noatime,data=ordered)
/dev/sde1 on /home/andre/FTP-Share/TV_Archive_G-R type ext4 (rw,noatime,data=ordered)
/dev/sde1 on /home/andre/FTP-ReadOnly/TV_Archive_G-R type ext4 (rw,noatime,data=ordered)
/dev/sdg1 on /mnt/5TB_2 type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-Share/Movies_New type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-Share/Movies_Archive_#-J type ext4 (rw,noatime,data=ordered)
/dev/sdc1 on /home/andre/FTP-Share/Movies_Archive_K-Z type ext4 (rw,noatime,data=ordered)
/dev/sdh1 on /home/andre/FTP-Share/TV_New type ext4 (rw,noatime,data=ordered)
/dev/sde1 on /home/andre/FTP-Share/TV_Archive_G-R type ext4 (rw,noatime,data=ordered)
/dev/sdg1 on /home/andre/FTP-Share/TV_Archive_S-Z type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-ReadOnly/Movies_Archive_#-J type ext4 (rw,noatime,data=ordered)
/dev/sdh1 on /home/andre/FTP-ReadOnly/TV_New type ext4 (rw,noatime,data=ordered)
/dev/sdg1 on /home/andre/FTP-Share/TV_Archive_S-Z type ext4 (rw,noatime,data=ordered)
/dev/sde1 on /home/andre/FTP-ReadOnly/TV_Archive_G-R type ext4 (rw,noatime,data=ordered)
/dev/sdg1 on /home/andre/FTP-ReadOnly/TV_Archive_S-Z type ext4 (rw,noatime,data=ordered)
/dev/sdh1 on /home/andre/FTP-ReadOnly/Marcus type ext4 (rw,noatime,data=ordered)
/dev/sdg1 on /home/andre/FTP-ReadOnly/TV_Archive_S-Z type ext4 (rw,noatime,data=ordered)
/dev/sdb1 on /mnt/4TB_2 type ext4 (rw,noatime,data=ordered)
/dev/sdb1 on /home/andre/FTP-Share/TV_Archive_#-F type ext4 (rw,noatime,data=ordered)
/dev/sdb1 on /home/andre/FTP-ReadOnly/TV_Archive_#-F type ext4 (rw,noatime,data=ordered)
/dev/sdb1 on /home/andre/FTP-Share/TV_Archive_#-F type ext4 (rw,noatime,data=ordered)
/dev/sdb1 on /home/andre/FTP-ReadOnly/TV_Archive_#-F type ext4 (rw,noatime,data=ordered)
/dev/sdf1 on /home/andre/FTP-ReadOnly/Movies_New type ext4 (rw,noatime,data=ordered)
/dev/sdc1 on /home/andre/FTP-ReadOnly/Movies_Archive_K-Z type ext4 (rw,noatime,data=ordered)

```

---

### Post by matt_symes on 2016-01-10
Hi
[B]
Edit:

I just rechecked and your mounts look good so follow the steps below.[/B]

We should disable automounting of USB disk to bypass udisks.

You are using Unity ? 

If so then open a terminal and copy and paste this into it.

```
dconf write /org/gnome/desktop/media-handling/automount false
```

Verify it's worked by copying and pasting this

```
dconf read /org/gnome/desktop/media-handling/automount
```

It should display *false*. If it doesn't display false then post back.

We can look at your kernel issues later but next we should fix samba and nfs for you.

Did you configure samba using the file /etc/samba/smb.conf ? This is the standard way so please post the output of

```
cat /etc/samba/smb.conf
```

and 

```
cat /etc/exports
```

Kind regards

---

### Post by andre46 on 2016-01-10
That command did end up in false.  I checked my bind mount folders, and everything appears to be copacetic there.

I updated samba and nfs while I was awaiting your response, so we're good on that already.  I've also updated most of my software that pointed at the media folder.

---

### Post by matt_symes on 2016-01-10
Hi

> **andre46 said:**
> That command did end up in false.  I checked my bind mount folders, and everything appears to be copacetic there.

I had to double check them. I though there were some missing but apparently I'm going blind :)

> I updated samba and nfs while I was awaiting your response, so we're good on that already.  I've also updated most of my software that pointed at the media folder.

You can check the samba shares with 

```
smbtree -N -b
```

and browse on a client with

```
smbclient \\\\<serverIP\\<share_name> -U <user_name> -W
```

if you want to verify from the command line or you can use Nautilus.

And you can check the NFS exports on the server with

```
showmount -e 127.0.0.1
```

Are your FTP configuration files correct and pointing to the correct location ?

How did you fix the black screen boot ? Did you boot into an older kernel ?

Kind regards

---

### Post by andre46 on 2016-01-10
Yeah, samba and nfs is all good - I had already confirmed that by just accessing the shares with my laptop.  And I connected to FTP with my phone, and everything looks good there.

Looks like we can attack the black screen issue, now (or tomorrow, since you're apparently signing off soon.  Yes - I booted to an older kernel, and that worked just fine.  Maybe I should just stop running updates and never reboot again haha

---

### Post by matt_symes on 2016-01-10
Hi

> **andre46 said:**
> Yeah, samba and nfs is all good - I had already confirmed that by just accessing the shares with my laptop.  And I connected to FTP with my phone, and everything looks good there.

Great :D

> Looks like we can attack the black screen issue, now (or tomorrow, since you're apparently signing off soon.  Yes - I booted to an older kernel, and that worked just fine.  Maybe I should just stop running updates and never reboot again haha

That sounds good to me. 

Tomorrow we can get to the root cause of these kernel problems and ensure that when you reboot everything gets set up correctly.

I'll make sure I'm online for 9pm UTC tomorrow evening, if you like, and we can fix the final issues but, more importantly, make sure you system is stable and consistent after a reboot.

**EDIT:**

Another things to check is the permissions on the mounts to ensure you can write to them.

Kind regards

---

### Post by andre46 on 2016-01-10
Good point - I'll have to check the permissions for FTP tomorrow.  Looks like samba and NFS are good.  The server is a bit bogged down right now trying to catch up on everything it missed in the past week :)

Actually, with my schedule tomorrow, I can be online at 11pm UTC.  Hope that's not too late!!!

---

### Post by matt_symes on 2016-01-11
Hi

> **andre46 said:**
> Good point - I'll have to check the permissions for FTP tomorrow.  Looks like samba and NFS are good.  The server is a bit bogged down right now trying to catch up on everything it missed in the past week :)

Actually, with my schedule tomorrow, I can be online at 11pm UTC.  Hope that's not too late!!!

11pm may be a bit late for me during the working week but I'll be online late over the weekend.

We are definitely on different time zones :)

Kind regards

---

### Post by andre46 on 2016-01-11
No problem.  I will be home all weekend, so we can knock this out on Saturday morning.  I'll just be sure to not reboot haha.  Thanks!

---

### Post by andre46 on 2016-01-15
I can be online around 4pm UTC (12 hours from the time of this post), and available for about 12 hours after that.  Let me know what works for you!  Thanks!

---

