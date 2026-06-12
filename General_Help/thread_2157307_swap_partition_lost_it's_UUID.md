---
title: "swap partition lost it's UUID"
date: 2013-06-24
forum: General Help
---

### Post by durduvakis on 2013-06-24
I would like some help if possible on how to fix this,
I am running ubuntu 12.04 desktop i386 on my laptop, I use it as a webserver,
 I didn't know my swap lost it's UUID until I tried to fix an issue with the plymouth boot screen and got this warning:
```

sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda5

```

/dev/sda5 is the swap partition as shown here, as you can see it has no UUID:
```

blkid
/dev/sda1: LABEL="WinXP" UUID="3464DDD564DD99C6" TYPE="ntfs" 
/dev/sda2: UUID="50be46ad-efa9-4e6c-a58f-c97218cd935b" TYPE="ext3" 
/dev/sda5: TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="60D8362AD835FF3A" TYPE="ntfs" 

```

this is my fstab
```

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda2 :
UUID=50be46ad-efa9-4e6c-a58f-c97218cd935b    /    ext3    errors=remount-ro,usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0    0    1
#Entry for /dev/sda6 :
UUID=60D8362AD835FF3A    /media/DATA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0
#Entry for /dev/sda1 :
UUID=3464DDD564DD99C6    /media/WinXP    ntfs-3g    defaults,locale=en_US.UTF-8    0    0
/dev/sda5    none    swap    sw    0    0

```

```

free -m
             total       used       free     shared    buffers     cached
Mem:          2011       1827        184          0         38        739
-/+ buffers/cache:       1050        961
Swap:         5122          0       5122

```

```

cat /proc/swaps
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       5245184 0       -1

```

I suspect what has caused this might be a partition resize I did on all partitions of this computer, using an app on windows xp, this might have damaged it.
I searched the net but all cases I found are different and I would not like to risk experiments on my own in this area.

Thanks for any help in advance.

---

### Post by Bashing-om on 2013-06-24
durduvakis; Hi !

Allow me to push this along a bit:
Post the output of terminal codes:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print

``` will show the layout of your disk, and what the partitioning scheme is.

Hopefully won't be so much that "/sbin/mkswap" can not take care of. (Hey, it's a thought)
[INDENT=2]
a tale is told in the telling

[/INDENT]

---

### Post by durduvakis on 2013-06-24
hey thanks for your time and help Mr  [                                                      [IMG]http://ubuntuforums.org/customavatars/avatar1111508_1.gif[/IMG]                                              ]("http://ubuntuforums.org/member.php?u=1111508")                                                                                     [**[COLOR=#000000]Bashing-om[/COLOR]**]("http://ubuntuforums.org/member.php?u=1111508") !

this is what you asked:

```

fdisk -lu
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x76af978d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          70    73400984    36700457+   7  HPFS/NTFS/exFAT
/dev/sda2        73400985   239159654    82879335   83  Linux
/dev/sda4       239159655   312576704    36708525    f  W95 Ext'd (LBA)
/dev/sda5       239159718   249650099     5245191   82  Linux swap / Solaris
/dev/sda6       249650166   312576704    31463269+   7  HPFS/NTFS/exFAT

```

```

sudo parted -l
Model: ATA WDC WD1600BEVS-0 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      35.8kB  37.6GB  37.6GB  primary   ntfs            boot
 2      37.6GB  122GB   84.9GB  primary   ext3
 4      122GB   160GB   37.6GB  extended                  lba
 5      122GB   128GB   5371MB  logical   linux-swap(v1)
 6      128GB   160GB   32.2GB  logical   ntfs

```


```

sudo parted /dev/sda unit s print
Model: ATA WDC WD1600BEVS-0 (scsi)
Disk /dev/sda: 312581808s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size        Type      File system     Flags
 1      70s         73400984s   73400915s   primary   ntfs            boot
 2      73400985s   239159654s  165758670s  primary   ext3
 4      239159655s  312576704s  73417050s   extended                  lba
 5      239159718s  249650099s  10490382s   logical   linux-swap(v1)
 6      249650166s  312576704s  62926539s   logical   ntfs

```

By the way, I read somewhere that swap partitions do not have UUID and now I am more confused..
thanks !

edit: Also, I was using grub-customizer and super-boot-manager that I removed some minutes ago because they messed things (or I did with them).. I got no idea what this cryptsetup is and I never encrypted anything except in php coding :D

---

### Post by Bashing-om on 2013-06-25
durduvakis; Hey..
Most assuradly swap should have a UUID : Here is my output of "blkid"

> sysop@1304mini:~$ sudo blkid
[sudo] password for sysop: 
/dev/sda1: LABEL="1304mroot" UUID="3a47f1f1-ed1f-4134-b6aa-be101a7d97b4" TYPE="ext4" 
/dev/sda2: LABEL="1304mhome" UUID="29a6fc4f-ff12-4cac-8eb1-e98e50f1107f" TYPE="ext4" 
/dev/sda5: UUID="192a4783-56fa-4fd0-a62f-c45a14c08482" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="3ad091a1-5036-463b-ba4e-88e98e41b07a" TYPE="ext4" 
/dev/sda7: LABEL="LUBU1204" UUID="4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d" TYPE="ext4" 
/dev/sda8: LABEL="1304mvar" UUID="136af805-5758-4880-acc4-0e1d35e2c266" TYPE="ext4" 
/dev/sdb1: LABEL="my_stuff" UUID="6a24777c-8191-4230-81f1-376f31b321e5" TYPE="ext4" 
/dev/sdc1: LABEL="ubie1204" UUID="5bae8c40-b15d-42f8-9fc9-0cf087f338d4" TYPE="ext4" 
sysop@1304mini:~$ 


So the question is why is there no UUID in your blkid output. Your partition output seems all in order.
Here is what I propose:
Edit the /etc/fstab file and replace the "/dev/sda5" with the UUID . so we need that UUID
```

ls /dev/disk/by-uuid -alh
sudo blkid /dev/sda5 -c /dev/null

```just to verify
Make the edit -> my example:
> 
UUID=192a4783-56fa-4fd0-a62f-c45a14c08482 none            swap    sw              0       0

now rebuild swap:
```

sudo swapoff -a
sudo /sbin/mkswap /dev/sda5
sudo swapon /dev/sda5
sudo mount -a ##no output here is good, means all is happy
sudo update-initramfs -u ##just to make sure the ramfs image is updated
swapon -s ## to see the status of swap

```

and I expect all is good to go. Are you prepared to (re-)boot and see what haps ?

[INDENT][INDENT]where there are solutions there are no problems[/INDENT][/INDENT]

---

### Post by durduvakis on 2013-06-25
hey friend, if I understood well, you asked me to take the UUID that I will find after running
```
ls /dev/disk/by-uuid -alh
```
but this command returns this:
```

total 0
drwxr-xr-x 2 root root 100 Jun 25  2013 .
drwxr-xr-x 6 root root 120 Jun 25  2013 ..
lrwxrwxrwx 1 root root  10 Jun 25 08:16 3464DDD564DD99C6 -> ../../sda1
lrwxrwxrwx 1 root root  10 Jun 25 08:16 50be46ad-efa9-4e6c-a58f-c97218cd935b -> ../../sda2
lrwxrwxrwx 1 root root  10 Jun 25 08:16 60D8362AD835FF3A -> ../../sda6

```

!?!?

---

### Post by Bashing-om on 2013-06-25
durduvakis;
Yeah .. something is very amiss; My Output ->
> 
sysop@1304mini:~$ ls /dev/disk/by-uuid -alh
total 0
drwxr-xr-x 2 root root 200 Jun 24 11:02 .
drwxr-xr-x 6 root root 120 Jun 24 11:02 ..
lrwxrwxrwx 1 root root  10 Jun 24 11:02 136af805-5758-4880-acc4-0e1d35e2c266 -> ../../sda8
lrwxrwxrwx 1 root root  10 Jun 24 11:02 192a4783-56fa-4fd0-a62f-c45a14c08482 -> ../../sda5
lrwxrwxrwx 1 root root  10 Jun 24 11:02 29a6fc4f-ff12-4cac-8eb1-e98e50f1107f -> ../../sda2
lrwxrwxrwx 1 root root  10 Jun 24 11:02 3a47f1f1-ed1f-4134-b6aa-be101a7d97b4 -> ../../sda1
lrwxrwxrwx 1 root root  10 Jun 24 11:02 3ad091a1-5036-463b-ba4e-88e98e41b07a -> ../../sda6
lrwxrwxrwx 1 root root  10 Jun 24 11:02 4e6cd96d-49bd-47f0-9dfe-8eeebad4cf9d -> ../../sda7
lrwxrwxrwx 1 root root  10 Jun 24 11:02 5bae8c40-b15d-42f8-9fc9-0cf087f338d4 -> ../../sdc1
lrwxrwxrwx 1 root root  10 Jun 24 11:02 6a24777c-8191-4230-81f1-376f31b321e5 -> ../../sdb1
sysop@1304mini:~$

To clear cache and get new view:
```
sudo blkid -c /dev/null -o list
##then
sudo blkid /dev/sda5 -c /dev/nul

```
yields us a valid UUID for swap partition sda5 ?

[INDENT][INDENT]fingers are crossed[/INDENT][/INDENT]

---

### Post by durduvakis on 2013-06-25
right after my previous reply I moved on and maybe did something silly. edited the fstab adding YOUR UUID there.
then I run those see what happened:
```

me@laptop:~$ sudo swapoff -a
me@laptop:~$ sudo /sbin/mkswap /dev/sda5
Setting up swapspace version 1, size = 5245184 KiB
no label, UUID=807a058d-278a-45f6-9bf0-27ff695119b9
me@laptop:~$ sudo swapon /dev/sda5
me@laptop:~$ sudo mount -a
me@laptop:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda5
swaponme@laptop:~$ 
me@laptop:~$ swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda5                               partition       5245184 208     -1

```

then I rebooted and while it was booting is threw a msg about drive not ready now I am back in.
I jsut run the commands you just said and got this:

```

sudo blkid -c /dev/null -o list
device                       fs_type     label        mount point                      UUID
---------------------------------------------------------------------------------------------------------------------------
/dev/sda1                    ntfs        WinXP        /media/WinXP                     3464DDD564DD99C6
/dev/sda2                    ext3                     /                                50be46ad-efa9-4e6c-a58f-c97218cd935b
/dev/sda5                    swap                     (not mounted)                    807a058d-278a-45f6-9bf0-27ff695119b9
/dev/sda6                    ntfs        DATA         /media/DATA                      60D8362AD835FF3A


sudo blkid /dev/sda5 -c /dev/null
/dev/sda5: UUID="807a058d-278a-45f6-9bf0-27ff695119b9" TYPE="swap" 

```

I will try a reboot till you respond back :D
thanks again

---

### Post by Bashing-om on 2013-06-25
durduvakis;

No harm done.. just screaming and hollering that the UUID is invalid... could not mount what can not be found.

Ok ... we in business now ?
what returns from a plain old ordinary blkid request:
```
sudo blkid
##and verify/confirmation
sudo blkid /dev/sda5 -c /dev/null

```[INDENT]
move'n on ?

[/INDENT]

---

### Post by durduvakis on 2013-06-25
I think its almost done if not already.



```

sudo blkid
/dev/sda1: LABEL="WinXP" UUID="3464DDD564DD99C6" TYPE="ntfs" 
/dev/sda2: UUID="50be46ad-efa9-4e6c-a58f-c97218cd935b" TYPE="ext3" 
/dev/sda5: UUID="807a058d-278a-45f6-9bf0-27ff695119b9" TYPE="swap" 
/dev/sda6: LABEL="DATA" UUID="60D8362AD835FF3A" TYPE="ntfs" 





sudo blkid -c /dev/null -o list
device                       fs_type     label        mount point                      UUID
---------------------------------------------------------------------------------------------------------------------------
/dev/sda1                    ntfs        WinXP        /media/WinXP                     3464DDD564DD99C6
/dev/sda2                    ext3                     /                                50be46ad-efa9-4e6c-a58f-c97218cd935b
/dev/sda5                    swap                     <swap>                           807a058d-278a-45f6-9bf0-27ff695119b9
/dev/sda6                    ntfs        DATA         /media/DATA                      60D8362AD835FF3A

```

```

sudo blkid /dev/sda5 -c /dev/null
/dev/sda5: UUID="807a058d-278a-45f6-9bf0-27ff695119b9" TYPE="swap"

```

my fstab
```

proc    /proc    proc    nodev,noexec,nosuid    0    0

#Entry for /dev/sda2 :
UUID=50be46ad-efa9-4e6c-a58f-c97218cd935b    /    ext3    errors=remount-ro,usrjquota=quota.user,grpjquota=quota.group,jqfmt=vfsv0    0    1

#Entry for /dev/sda6 :
UUID=60D8362AD835FF3A    /media/DATA    ntfs-3g    defaults,nosuid,nodev,locale=en_US.UTF-8    0    0

#Entry for /dev/sda1 :
UUID=3464DDD564DD99C6    /media/WinXP    ntfs-3g    defaults,locale=en_US.UTF-8    0    0

#Entry for /dev/sda5 :
##/dev/sda5    none    swap    sw    0    0
UUID=807a058d-278a-45f6-9bf0-27ff695119b9 none swap sw 0 0

```

As you see I added "807a058d-278a-45f6-9bf0-27ff695119b9" to the fstab and rebooted too.
The only thing that looks weird still is this:
```

sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda5

```

any suggestions ?

---

### Post by Bashing-om on 2013-06-25
durduvakis; Totally unexpected !

Ok.. you did the swap rebuild routine ?
then lets see what is:
```

sudo dmsetup status ## "no devices found" is good
ls -ld /dev/mapper/cryptswap1 ##"cannot access" is good
ls -ld /etc/crypttab ##"cannot access" is good

```[INDENT=2]
gotta be a reason

[/INDENT]

---

### Post by durduvakis on 2013-06-25
you an expert !

```

me@laptop:~$ sudo dmsetup status
No devices found

me@laptop:~$ ls -ld /dev/mapper/cryptswap1
ls: cannot access /dev/mapper/cryptswap1: No such file or directory

me@laptop:~$ ls -ld /etc/crypttab
-rw-r--r-- 1 root root 54 Apr 20 13:38 /etc/crypttab

```

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]durduvakis;

It is amazing to me what I DO NOT know...sometimes what I do not know bites real bad, others, what I think I know bites even more !

For this one:
fire up a text editor ..I prefer gedit and:
[/COLOR]```

gksudo gedit /etc/crypttab
*remove the /dev/sda5 line*

```
also want to see what is:
```

ls -la /dev/mapper
cat /etc/uswsusp.conf

```[INDENT=2]and again a tale in the telling

[/INDENT]

---

### Post by durduvakis on 2013-06-25
what I have learned most of all, is that the more I learn the less I know.
thanks for your help indeed.

I have been in /etc/crypttab previously and has nothing:
```

gksudo gedit /etc/crypttab
# <target name>    <source device>        <key file>    <options>

```

```

ls -la /dev/mapper
total 0
drwxr-xr-x  2 root root      60 Jun 25  2013 .
drwxr-xr-x 15 root root    4280 Jun 25 09:15 ..
crw-------  1 root root 10, 236 Jun 25 08:58 control

```

```

cat /etc/uswsusp.conf
cat: /etc/uswsusp.conf: No such file or directory

```

---

### Post by Bashing-om on 2013-06-25
durduvakis; Well well ..
I like what I see, so:
```

sudo update-initramfs -u -k all

```
(re-)boot and lets see you up and running ![INDENT=2]
where there are solutions there are no problems

[/INDENT]

---

### Post by durduvakis on 2013-06-25
so before reboot:

```

sudo update-initramfs -u -k all

update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic-pae
cryptsetup: WARNING: failed to detect canonical device of /dev/sda5
update-initramfs: Generating /boot/initrd.img-3.2.0-48-generic
cryptsetup: WARNING: failed to detect canonical device of /dev/sda5

```

After reboot the same !
Something must have gone wrong when that kernel update (3.2.0-43) failed and I had to reinstall it.
And in fact I did not see any kernel updates to 3.2.0-48 until I saw them yesterday in synaptic.
The systm was excellent what has gone wrong I dunno !

---

### Post by Bashing-om on 2013-06-25
durduvakis;

Well,, As Your machine is a laptop lets look at what is in the resume config file:
```

cat /etc/initramfs-tools/conf.d/resume:

```
I am considering moving the crypttab file out of the picture and see what results.
And you may have a point about the new kernel... but before we throw stones at it ... what happens if you boot up from a prior kernel ?


[INDENT][INDENT]now I am wondering [/INDENT][/INDENT]

---

### Post by durduvakis on 2013-06-25
```

cat /etc/initramfs-tools/conf.d/resume
RESUME=/dev/sda5

```

I would love to try to boot from a previous kernel version, but I got this bad habit to uninstall them ( :D ).
Installing some from synaptic may work ?

and I will try to remove the crypttab file to test.

EDIT: guess what, I commented out #RESUME=/dev/sda5 from /etc/initramfs-tools/conf.d/resume and run sudo update-initramfs -u without any error !
If I say I understand what is goinf on I will be a big liar

EDIT 2: I suspect hybernation ? I have never enabled something like this ... maybe KDE added such things

---

### Post by Bashing-om on 2013-06-25
durduvakis;
Always have a back up ...huh ..
anyway .. no likey resume ... make it:
```

RESUME=/dev/disk/by-uuid/807a058d-278a-45f6-9bf0-27ff695119b9

```
And rather than removing crypttab ...move it ... a mv is easier to reverse.

[INDENT][INDENT]maybe maybe[/INDENT][/INDENT]

---

### Post by durduvakis on 2013-06-25
I changed the resume file contents to what you adviced teacher, and renamed the crypttab file to crypttab.backup.
It is now rebooting.
It is fixed now right ? shall I open beers ? but you are on the other side of the planet ! :D
how can I thank you !

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]durduvakis;

All is good now ?
just to KNOW all is good do:
```

sudo update-grub

```
[/COLOR][INDENT=2][COLOR=#000000]all's well that ends well

[/COLOR][/INDENT]

---

### Post by durduvakis on 2013-06-25
```

sudo update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-48-generic-pae
Found initrd image: /boot/initrd.img-3.2.0-48-generic-pae
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found Design System on /dev/sda1

```

it should be ! I am on this since last night.. I even forgot what I wanted to do before I found out about this mess.
I think it booted faster this time.

---

### Post by Bashing-om on 2013-06-25
[COLOR=#000000]durduvakis; Hey !

Booting: yes it will be a tad bit faster.. using the UUIDs rather than device names, lessens the hoops the system has to jump through. More direct is better.

Let us then close this out... it is 4 AM my time ... and my bed is calling long time past.
Thanks to me is for you to pass on to others what knowledge you have .. maybe to me next time ! Perhaps frequent this forum and respond to another's need ..passing your knowledge on !

[/COLOR]Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.
[INDENT=2]
and hey, it's ubuntu ! our operating system by choice[/INDENT]
[COLOR=#000000]

[/COLOR]

---

### Post by durduvakis on 2013-06-25
Thanks for everything man I really appreciate, and thanks for having the spirit everyone should !
I go mark it solved :D
cheers !

---

