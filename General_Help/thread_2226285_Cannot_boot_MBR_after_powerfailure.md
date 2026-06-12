---
title: "Cannot boot MBR after powerfailure"
date: 2014-05-26
forum: General Help
---

### Post by BigBaka on 2014-05-26
Hi,

I'm running Ubuntu 14.04 64bit on a desktop in Yangon Myanmar where there are frequent power outages. I just moved here and am yet to buy a UPS power stabilizer to protect the computer when power outages happen, and after one too many consecutive power outages I'm now unable to boot the computer. When i try to boot the bios loads fine, but then fails to boot into the MBR. The error message on the screen simply says "Read Error" and I can't do anything. Is there a way to recover this, or will I have to reinstall? I have a separate partition for the root drive and for the /home, so if recovery is overly difficult, reinstall is an option although setting all the software up again would be a right pain in the behind.

Thanks for your help.

Regards,
BigBaka

---

### Post by dragonfly41 on 2014-05-26
Have you tried "recovery mode" in Grub menu when booting up?

---

### Post by BigBaka on 2014-05-26
Nope, is there a way to force recovery mode?

---

### Post by oldfred on 2014-05-26
You have to get to grub menu to see recovery mode. If you only have one system installed you do not normally get grub menu and if BIOS hold shift key from BIOS screen until menu appears.

It also may just be some corruption that fsck will fix. You may need to run on both boot & main install partitions.

 #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by BigBaka on 2014-05-26
Couldn't get to the GRUB menu. Pressing shift in BIOS, displayed "GRUB loading", then after about 5 seconds the same "Read Error" message.

---

### Post by oldfred on 2014-05-26
You have to hold shift key from BIOS until menu appears.

But you may just need to run the fsck from a live installer.

---

### Post by Bashing-om on 2014-05-26
BigBaka; Hi !

Appears that the boot code is corrupted, as you can not get the grub menu. 
Try and (RE-)install grub.
This "assumes" you did a standard install of ubuntu, and it is the sole operating system and, ubuntu is installed onto the 1st partition of that 1st (only ?)hard drive.

Boot up the liveDVD and from the liveDVD issue these terminal commands.
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda ##because in this instance we want Grub installed to the MBR of drive 'sda'
sudo umount /mnt

```

OK ??., Now boot into the install ( reset the boot priority as needed) to a terminal and:
verify/recheck grub:
terminal commands:
```

sudo grub-install --recheck /dev/sda
sudo update-grub

```

(RE-)boot once more to insure all is now good.

[INDENT][INDENT]this ain't nothing
[INDENT][INDENT][INDENT]but a thing
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-27
Hi,

Thanks for the tips, am now loading the live DVD to attempt the rescue. For the record my partition is as per this tutorial though of course sizes are somewhat different.
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by BigBaka on 2014-05-27
> #From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

In trying to do the above I got the following
```

ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?
```

I did however manage to install grub, and am now going to see if i can reboot into the hard drive.

BB

---

### Post by BigBaka on 2014-05-27
after installing GRUB on sda1 using a live CD, i tried to reboot, but got the same Read Error message.

Pressing shift during reboot, made the word GRUB appear on the screen, but then after about 5-10 seconds the same Read Error message appeared. Any ideas?

Regards,
BB

---

### Post by Bashing-om on 2014-05-27
BigBaka; Well, not what we had hoped to see.

Show us what we are working with to remove any lingering doubts of the perscribed procedures.
post back the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```

And will see what else might be done.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]othertimes I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by mdurham on 2014-05-27
I would say that if the MBR is screwed up, there is no way to get to GRUB. What I would do as I'm a simple person is: Do a full install to a USB stick. After rebooting to the USB stick you should see the system on the hard drive in the GRUB menu and be able to boot into it from the GRUB menu on the USB stick.
There may be quicker ways of doing this, but that's all I know.
Good luck

---

### Post by oldfred on 2014-05-27
Run the commands in Post #11 suggested by Bashing-om.

---

### Post by BigBaka on 2014-05-29
Here is the read out

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97656831    48827392   83  Linux
/dev/sda2        97658878   976771071   439556097    5  Extended
/dev/sda5        97658880   102539263     2440192   82  Linux swap / Solaris
/dev/sda6       102541312   976771071   437114880   83  Linux

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1711

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7935999     3967969    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  500GB   450GB   extended
 5      50.0GB  52.5GB  2499MB  logical   linux-swap(v1)
 6      52.5GB  500GB   448GB   logical   ext4


Model: Kingston DT 101 II (scsi)
Disk /dev/sdb: 4063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4063MB  4063MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ 
```

---

### Post by Bashing-om on 2014-05-29
BigBaka; OK, Work,

This:
> 
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
e2fsck: Attempt to read block from filesystem resulted in short read while trying to open /dev/sda1
Could this be a zero-length partition?

Makes me suspect a bad superblock.

We have run file system check that failed;
We have installed grub to the proper location of the MBR of sda that failed;

So, how about sparring off the superblock with one of the backups ?
Excellent instruction in slickymaster's thread:
[http://ubuntuforums.org/showthread.php?t=2177756](http://ubuntuforums.org/showthread.php?t=2177756)

That done, reboot and let's see what that result is.


If at 1st you do not succeed
[INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-29
Hi bashing om, 

Got this from the e2fsck command. Mean anything to you? So do you think I should now follow slickymasters thread, or does the info below tell us something useful?

```
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sda1
/dev/sda1:                                                                      Inode 2891983, end of extent exceeds allowed value
	(logical block 51, physical block 11567727, len 1)


/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
```

---

### Post by Bashing-om on 2014-05-29
BigBaka; Welp,

Wont hurt a thing to take heed of fsck's advise and see what results:
```

sudo e2fsck -f -y -v /dev/sda1

```
as we know that sda1 is the partition containing '/'. The -y auto answers yes for fixes needing response see: man e2fsck.
Depending, we can take matters into out own hands, but my "limited" experience says the system makes better decisions than I could about what to fix and how.

[INDENT]still worth a shot
[/INDENT]

---

### Post by BigBaka on 2014-05-29
```
ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Inode 2891983, end of extent exceeds allowed value
	(logical block 51, physical block 11567727, len 1)
Clear? yes

Pass 2: Checking directory structure
Entry 'avahi-daemon.log' in /var/log/upstart (2891974) has deleted/unused inode 2893021.  Clear? yes

Entry 'flush-early-job-log.log' in /var/log/upstart (2891974) has deleted/unused inode 2893020.  Clear? yes

Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Unattached inode 1311928
Connect to /lost+found? yes

Inode 1311928 ref count is 2, should be 1.  Fix? yes

Pass 5: Checking group summary information
Block bitmap differences:  -(9410--9411) +(323584--327679) +(329728--331775) +(356352--359167) +(380928--385174) -(1581089--1581094) -9469990 +9470059
Fix? yes

Free blocks count wrong (10832282, counted=10833528).
Fix? yes

Inode bitmap differences:  -(393218--393499)
Fix? yes

Free inodes count wrong (2865331, counted=2865613).
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

      190003 inodes used (6.22%, out of 3055616)
         110 non-contiguous files (0.1%)
         275 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 144445/29
     1373320 blocks used (11.25%, out of 12206848)
           0 bad blocks
           1 large file

      113029 regular files
       15554 directories
          57 character device files
          25 block device files
           0 fifos
           4 links
       61326 symbolic links (45436 fast symbolic links)
           3 sockets
------------
      189997 files
```

Time to restart then?

---

### Post by Bashing-om on 2014-05-29
BigBaka; Hey;

Looks as if 'e2fsck' did do something, hope the magic worked !

Yeah, reboot and let's see what the result is.

[INDENT][INDENT]it could happen
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-29
Bashing-om;

Well the good news is the error on boot up has progressed from "Read Error", the bad news is it is still not booting. Upon restart i get the following

```
error: file '/grub/i386-pc/normal.mod' not found
Entering rescue mode...
grub rescue> 
```

with a flashing cursor. Any advise about what to try now?

Many thanks
BB

---

### Post by Bashing-om on 2014-05-29
BigBaka; Hey !

Now that is good news.
The "'/grub/i386-pc/normal.mod' not found" is in all likely hood fixable.

Let's try the easier method 1st>
try once more the procedure from post #7.

Else, well there are a couple of other avenues we can explore to get grub's files restored.

I do prefer the "easier" less intrusive methods.

[INDENT][INDENT]1st things 1st
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-29
So the reinstall seemed to work fine. No errors of any kind reported.


However, upon restart the computer loaded into GRUB and them came to a complete halt. On my screen I have

GNU GRUB version 2.02 beta2-9

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

grub> 

again a flashing cursor aka dos.

Perhaps I needed to load the live CD again?

---

### Post by Bashing-om on 2014-05-29
BigBaka; Maybe .. but

Let's see what results:
at the grub boot menu ; press the 'c' key for a command line:
at the resulting grub > prompt
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)initrd.img
boot

```

See if we can boot in this manner into the install, and maybe then re-do grub ?

[INDENT][INDENT]where there is a will we will find a way[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-29
> **Bashing-om said:**
> BigBaka; Maybe .. but

Let's see what results:
at the grub boot menu ; press the 'c' key for a command line:
at the resulting grub > prompt
```

linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)initrd.img
boot
```


Sorry, i'm not sure what you mean here. There is no grub boot menu, just the grub> prompt

I typed in your first line of code only to get
```

error: file '/ymlinuz' not found.
```

Think I'm going to sleep on this for the moment. If you have any other ideas, please let me know and I'll try again tomorrow.

Cheers,
BigBaka

---

### Post by Bashing-om on 2014-05-29
BigBakal OK,

Rest well, and we will pick this back up at a later time.
And, yeah, we are working at that "grub >" prompt .. we can do this.

for now double check that your "ymlinuz" is not my "vmlinuz".
And if still " file not found" we tell the boot manager where that file is, and then see what happens.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-30
Bashing-om;

Back again, though it is 3am in the morning here! Perfect time for computer maintenance! 
Sorry about the typo, you're right I typed the wrong command in grub.

the vmlinuz command seemed to work fine. However, initrd did not. Came up with the error 
```

error: invalid file name 'initrd.img'

```

---

### Post by Bashing-om on 2014-05-30
BigBaka; Well.

Let's tell the boot manager where those files are and try to boot once more.

at that grub > prompt
```

set root=(hd0,msdos1)
set prefix=(hd0,msdos1)/boot/grub
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
insmod normal
boot

```
Do you now boot ? 
OR
I would not be terribly surprised if we need to dig deeper and do some other directing for file location(s). I DO know how to look and find them.

Upfront - from personal experience - it "can" be a real pain to find the file(s) at fault and find a means to repair them.

The better news is that it can be done

[INDENT][INDENT]tis a puzzle in the solving
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-30
Hi, it seems to be booting now. But at 2.6 seconds it had a long wait. Eventually at 140 seconds it came up with "random: nonblocking pool is initialized". Presently suspended again processing something. Will let you know how it goes. 

Your knowledge on this stuff is amazing.

Cheers
BB

---

### Post by Bashing-om on 2014-05-30
BigBaka; Alright !

As we now know how to boot the system, we need to fix it to boot from the grub boot menu normally.

SO, ya want to keep trying to isolate the exact fault, or
Take the sledge hammer approach and rebuild (most) of the files used in the boot process, and be done with this  ? 


[INDENT][INDENT]believe me
[INDENT][INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-30
After 15 minutes with no activity I finally did a forced shut down. Computer reloaded back into grub prompt. typing boot gave the error
```
error: you need to load the kernel first
```

---

### Post by BigBaka on 2014-05-30
ran commands again, and various errors coming up 
such as exception Emask 0x0
familed command: READ DMA
ata3.01: device reported invalid CHS sector 0
ata3: EH complete
ata3: lost interrupt
ata3: link is slow to respond, please be patient
device not read, forceing hardreset
revalidaiton failed
configured for UDMA/100
device reported invalid CHS sector 0
EH complete

appears to be stuck in a loop doing this and other things.

---

### Post by BigBaka on 2014-05-30
Now stuck in a very quickly processing error loop that is hard to make out the error messages but some of them look like
phython main process (xxxxxxx) killled by BUS signal
booting terminated re-trying

it doesn't look good

---

### Post by BigBaka on 2014-05-30
Managed to cntrl C break the loop, 

Error messages as such
```

init: mountall-shell post-stop process (xxxxxxxx)killed by INT signal
init: Failed to spawn console-setup process: unable to execute: Input/output error
init: plymouth main process (xxxxxxx) killed by BUS signal
init: Error while reading from descriptor: Bad file descriptor
init: mountall-shell main process (xxxxxxx) killed by INT signal
init: mountall-shell post-stop process (xxxxxx) killed by INT signal
init: mountall main process (xxxxxxx) terminated with status 2

```

---

### Post by Bashing-om on 2014-05-30
BigBakal Shucks ...
I had thought we had made grater progress.

Looks like the system is not happy with the kernel-image.
But, let's poke at it a bit more.

OK. lets look and and see if those files grub is hollering about are in place:
at that grub > prompt do:
```

ls -la (hd0,msdos1)/vmlinuz
ls -la (hd0,msdos1)/initrd.img
ls -la (hd0,msdos1)/boot/

```
The 1st two should be symbolic links - such as: ( vmlinuz -> boot/vmlinuz-3.11.0-22-generic)
and what we want is the file and version number that is pointed to by both vmlinuz and initrd.img
and the last to see that they are in fact there.

Also let's see if grub's configuration file is present:
```

search -f /vmlinuz
search --set=root --file /boot/grub/grub.cfg

```
and If both these return positive results we know the "paths" are set. ( or not ).

If we can ever get this sucker booted, we can take measures to repair the booting.
Else, welp - it is ubuntu, there are always alternatives,,, we can do a full change root into the install from the liveDVD and try and fix the boot code from there.

For now, with the info from the above will try and boot the install .

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-30
Ok, I'm seriously getting lost now.

Well the readout after the first 3 commands is
```
DIR                               20140516162612 ./
DIR                               20140529162926 ../
DIR                               20140512150309 grub/
3372643                        20140503003029 System.map-3.13.0-24-generic
1158016                        20140503003028 abi-3.13.0-24-generic
165510                          20140503003028 config-3.13.0.24-generic
176500                          20140312123109 memtest86+.bin
178176                          20140312123109 memtest86+.elf
178680                          20140312123109 memtest86+_multiboot.bin
5776416                        20140503003028 vmlinuz-3.13.0-24-generic
19090298                       20140516162612 initrd.img-3.13.0-24-generic
```

The search -f /vmlinuz command came up
```
hd0,msdos1
```

The last search --set=root --file /boot/grub/grub.cfg command seemed to work fine.

Guess I'll now try and boot again.

---

### Post by BigBaka on 2014-05-30
typing boot returned the same kernel error as before
```
error: you need to load the kernel first
```

---

### Post by Bashing-om on 2014-05-30
BigBaka; UMMpphh,

Not what I had expected to see on those 1st 2 commands. Lemme reboot my system to the grub prompt and re-confirm what we should be seeing.

All we are doing right now is looking to see that files are present and in place such that the booting operation will proceed. If these files are not present, welp we got to make it so.


Be back in a bit.

[INDENT][INDENT]it is in the process
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-05-30
BigBaka; Hey ,

I have been looking.
this result of yours;
> 
error: you need to load the kernel first
 bothers me just a bit as to why it no longer sees the kernel.

At that grub > prompt do:
```

set

``` this will display what grub has 'set' for defaults.
In that output do you see:
have_grubenv=true
prefix=(hd0,msdos1)/boot/grub
root=hd0,msdos1

else we will just have to set some parameters so the boot manager knows where the files are . We can do that.

[INDENT][INDENT]the mysteries of booting an operating system
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-05-31
there is no have_grubenv

```
prefix=(hd0,msdos1)/grub
```
is different to what you have

```
root=hd0,msdos1
```
is the same as you

also I'm not sure if it is important but some items have no values at all

lang=
locale_dir=
pager=
secondary_locale_dir=

---

### Post by Bashing-om on 2014-05-31
BigBaka; Alright ;

Still looking to see what files are where so we have some idea of what it is going to take to boot the kernel.
So, let's look at what we have to work with and where !
grub > prompt
```

ls -la (hd0,msdos1)/vmlinuz
ls -la (hd0,msdos1)/initrd.img
ls -la (hd0,msdos1)/boot/grub/gub.cfg

```
IF all 3 of the above return with positive results, Then let's try and boot:
```

set prefix=(hd0,msdos1)/boot/grub
set root=(hd0,msdos1)
insmod linux
linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
initrd (hd0,msdos1)/initrd.img
boot

```

I am not at all sure of what a 'locale' not set will produce. Maybe "inserting the module" 'linux' will resolve this ?

Now if these files above are in place AND grub.cfg is not corrupted, then it should boot !

Let's see.

If we can ever get this sucker to boot and get to a place where we can (re-)install grub we will be in good shape.

[INDENT][INDENT]just try'n to make it happen
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-06-01
Hey Bashing-om,

Alas, was going so well, but came back with error on 3rd last command (which looks like the key one)
```
grub> linux (hd0,msdos1)/vmlinuz root=/dev/sda1 ro
error: attempt to read or write outside of disk 'hd0'
```

---

### Post by Bashing-om on 2014-06-01
BigBakalL UUHHH !

Now that is UnGood !

Partition table messed up, partitioning scheme hosed up ?? Humm. Don't know.

Fire up the liveDVD to terminal and lets look at what is:
```

sudo fdisk -lu
sudo parted -l

```

[INDENT][INDENT]'till we know
[INDENT][INDENT][INDENT]can't say
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-06-01
BigBaka:
Hey,

I am done for this session. My eyes are crossing and the mind is fuzzy.

Will see what is - in my Am and we go again.

[INDENT][INDENT]can't stands no more
[/INDENT][/INDENT]

---

### Post by BigBaka on 2014-06-01
Bashing-om;

No worries, will catch you in the morning, in the meantime, here is the readout

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1711

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          62     7935999     3967969    c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudo parted -l
Model: Kingston DT 101 II (scsi)
Disk /dev/sda: 4063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4063MB  4063MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label     
```

---

### Post by oldfred on 2014-06-01
That is only showing a 4GB flash drive? And it is formatted FAT32, and if all along has been your sda would explain all the errors.
Where is your hard drive?
Does BIOS show a hard drive?

---

### Post by BigBaka on 2014-06-01
Oldfred;

Yes, you're right. Actually my hard drive and or motherboard sometimes give me problems by disappearing. I've never been able to work out what it is from. Often I just adjust the connections between hard drive and motherboard again and it's right. However, the previous readouts couldn't be causing these errors when I was using Grub prompt because the usb drive wasn't plugged in. I only use the USB drive to boot the liveCD.

That said, the hard disk has definitely disappeared. I just ran the bios and it wasn't there, but after opening up the box, a quick check of cables, and there it was again. But now that I've loaded the liveUSB I can't see the hard drive again. The two commands bring the same results. Opening disks utility brings a strange result. I get the usb systems, but at /dev/sda I get simply Block Device with no size. Not sure if my hard drive is screwed or if this is something to do with what I have been doing above.

---

### Post by BigBaka on 2014-06-01
See the screen shot 

[ATTACH=CONFIG]253647[/ATTACH]

---

### Post by oldfred on 2014-06-01
If Ubuntu does not see internal hard drive then flash drive will be sda.
Disks should be showing a XXX GB Hard Disk device where XXX is the size.

Is drive SATA or IDE/PATA?

I used to have many issues with IDE drives, so totally converted to SATA when they become only a few dollars more than PATA drives. I could not open case and not bump the wide IDE cable/connector. And many times it would looks connected, but only partially. And then I cannot not tell you how much I hated all the little tiny jumpers for master, slave or cable-select.

---

### Post by BigBaka on 2014-06-01
Yet i can load up Grub? How am I doing that?

Looks like it is a SATA drive.

---

### Post by BigBaka on 2014-06-01
Restarted and low and behold there is my harfd drive again. The Block thing has gone from my disk utility. Following is readout of two prior commands.

```
ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000a6c2e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    97656831    48827392   83  Linux
/dev/sda2        97658878   976771071   439556097    5  Extended
/dev/sda5        97658880   102539263     2440192   82  Linux swap / Solaris
/dev/sda6       102541312   976771071   437114880   83  Linux

Disk /dev/sdb: 4063 MB, 4063232000 bytes
125 heads, 62 sectors/track, 1024 cylinders, total 7936000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f1711

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          62     7935999     3967969    c  W95 FAT32 (LBA)

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST3500418AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  50.0GB  50.0GB  primary   ext4            boot
 2      50.0GB  500GB   450GB   extended
 5      50.0GB  52.5GB  2499MB  logical   linux-swap(v1)
 6      52.5GB  500GB   448GB   logical   ext4


Model: Kingston DT 101 II (scsi)
Disk /dev/sdb: 4063MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      31.7kB  4063MB  4063MB  primary  fat32        boot, lba


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label    
```

---

### Post by oldfred on 2014-06-01
When you ran the fsck from early post, was 500GB drive visible? 

Error message was more like it was trying to run on a non-Linux formatted drive like your flash drive.
I might try the full e2fsck again on both sda1 & sda6.

---

### Post by Bashing-om on 2014-06-01
BigBaka; Morning .
@ oldfred, really nice to have you pop in here also !!

In addition to oldfred's advise to check the software, let's do what we can to check the hardware.

Check all the connections on all the wiring coming from the power supply, a great thing is "contact cleaner" - tech-in-a-spray-can - !
Sparingly spay the connections, and work them in and out, any connection that does not feel tight -- (or loose) might gingerly apply a pair of pliers to  tighten up that connector. Then when done, wire ties to take care of any "dangling" loose wires such that vibrations do not cause a "bad" connection.

Once all this is done, we go back to trying to see where the fault is ( software wise ) to get the system to boot.


From point a, to point b, to point c ->
[INDENT][INDENT][INDENT]it is all a process
[/INDENT][/INDENT][/INDENT]

---

### Post by BigBaka on 2014-06-09
Hi Bashing-om and Old Fred,

Just to let you know after cleaning some connections I retried the commands from post 40 and it all worked. Following the boot I ran 

sudo grub-install --recheck /dev/sda
sudo update-grub

which also seemed to go off without a glitch. I then restarted the comp and it booted! Low and behold! However, there are multiple errors coming up, seems related to software update, as well as apport.gtk and some others. Is there a way to check a log to see the errors to try and troubleshoot?

Cheers,
BB

---

### Post by oldfred on 2014-06-09
But if on update then run these: (# is comment, do not copy)

 #houseclean
sudo apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get clean

 sudo apt-get update 
sudo apt-get upgrade 

 #dist-upgrade is also able to remove existing packages if required
sudo apt-get dist-upgrade
# fix Broken packages -f 
sudo apt-get -f install
sudo dpkg --configure -a

---

### Post by BigBaka on 2014-06-09
Hi Old Fred,

Got stuck on the first command
```
glenn@glenn-desktop:~$ sudo apt-get autoclean
[sudo] password for glenn: 
Reading package lists... Done
glenn@glenn-desktop:~$ e... 0%
```

It just hangs there like that

At first when I did it it came up with an unexpected error message. Now it doesn't. Software manager also doesn't load

---

### Post by oldfred on 2014-06-09
Perhaps it crashed after last failure. It writes a lock so you cannot run two updates. I often open synaptic and then try to run a command update and it will not let me since it is locked.
If it did not close normally lock may still be there.

 Locked dpkg - only if sure you are not running another update. Software manager, synaptic or terminal all may lock it.
sudo rm /var/lib/dpkg/lock
sudo dpkg --configure -a

---

### Post by BigBaka on 2014-06-15
Old Fred, 

Thanks those commands did the trick. Everything running smooth now, no errors. 

Much thanks to you and especially to bashing-om for all the help getting things back online! Now I've got to go out and buy that UPS unit!

Cheers
BigBaka

---

### Post by Bashing-om on 2014-06-15
BigBaka; Great !

Pleased ya up and running !

[INDENT][INDENT]all's well that ends well
[/INDENT][/INDENT]

---

