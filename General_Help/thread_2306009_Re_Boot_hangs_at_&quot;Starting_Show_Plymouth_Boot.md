---
title: "Re: Boot hangs at &quot;Starting Show Plymouth Boot Screen&quot;"
date: 2015-12-11
forum: General Help
---

### Post by andre46 on 2015-12-11
Last night I was doing some work on my lubuntu server.  I had about 2 months worth of updates that had piled up, so I started running all of them.  The process got halfway through, and then errored out.  I didn't give it much attention, since this has happened before.  I ran updates again, and it again got halfway through, and errored out again. Again - I didn't really think much of it, I figured I'd just reboot and try again.  It had been feeling a bit sluggish anyway.  Now I'm no longer able to get to the gui.  Everything seems to work fine on boot - I get the Lubuntu splash screen, and then one of the following 2 screens comes up ([http://i.imgur.com/4iQYATl.jpg]("http://i.imgur.com/4iQYATl.jpg?1") , [http://i.imgur.com/G4tTzeD.jpg]("http://i.imgur.com/G4tTzeD.jpg?1")), and it just hangs at "Starting Show Plymouth Boot Screen".  I did a bit of searching, and found most people have reported this as an intermittent error, so I tried a few more times, and it is not intermittent for me.  Any ideas??

Update:
I posted this to reddit as well, and was given some things to try out.

I was unable to get to Grub by holding shift at boot
I was unable to get to TTY by pressing ctrl+alt+F1 or ctrl+alt+F2 at the lubuntu splash screen

Maybe I'm doing something wrong...?
-Andre

---

### Post by Bashing-om on 2015-12-11
andre46; Hummm ....

Really need to get to a terminal at this point:
> 
I was unable to get to Grub by holding shift at boot

Is this a UEFI endowed system ? Then it is the escape key that grub looks for . As soon as the firmware screen clears repeatedly depress and release the escape key - there is but a 3 second window of opportunity .

elsewise, we do have a problem.

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-12
Ok!  I got into grub using esc.  Wish I had known that earlier.  I removed "quiet splash" from the linux line of grub and tried a boot, and my system hung here: [http://imgur.com/7NCDcWF](http://imgur.com/7NCDcWF)

But we can get to command line!  I was also given [this]("https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure") as an option.

---

### Post by Bashing-om on 2015-12-12
andre46; Good deal !

Making head way.

Ok let's isolate this to the X (GUI) layer .
See if you can boot the system to terminal:
 boot to grub -> 'e' key -> boot parameters screen.
In this screen arrow down to the line starting with "linux" and across to "quiet splash" .
replace quiet splash and ALL after with " systemd.unit=multi-user.target " with out the quotes.
Key combo clt+x to continue the boot process to TTY1.

Log in here on this terminal with username and password.

Now let's see what the system does when we start the GUI:
```

systemctl isolate graphical.target

```
depending here on what results is what we do next and what logs to start looking over .

[INDENT][INDENT]the longest journey
[INDENT][INDENT][INDENT]even with small steps
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
I've tried logging in to that terminal a few times now, and I can't seem to get in.  When typing username, the characters don't show up, and upon pressing enter, the cursor moves to the beginning of the line, under the "N" of "NAS login".

---

### Post by Bashing-om on 2015-12-13
andre46; Well !

That ain't good .

What are we doing ? :
> 
the cursor moves to the beginning of the line, under the "N" of "NAS login".

where "NAS" is Network Access Storage ?? 
Are you accessing the server remotely ?
OR
Do we have keyboard driver issues ?
OR
Do we have file system problems and need to fire up a live environment and run a file system check/repair ? - not a bad idea to do so in any case in my humblest of opinions .

Until such time as we can activate a terminal -----
[INDENT][INDENT][INDENT]we are dead in the water
[/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
NAS is simply the device's name.  It lives in my basement, and I have a basic wired keyboard and wired mouse connected to the physical device - the keyboard is working just fine while editing grub.

---

### Post by Bashing-om on 2015-12-13
andre46; Hummm....

OK, Bios ? Though we have nothing to show that anything has happened to effect bios, the symptoms are similar.
"IOMMU Controller" ?. Insure it is Set to "Enabled" ;
Plug and play OS is set to enabled
USB devices .. maybe set to "legacy" .

Or maybe we have a bug in the latest kernel you have installed .. from the grub screen what results in attempting to boot other older kernels ?

Keeping in mind, still might be a great thing to do to run a file system check repair from a live environment ( liveDVD). If one has the liveDVD on hand easy and quick enough to do, to rule out a file system problem.

[INDENT][INDENT]fault isolation
[INDENT][INDENT][INDENT]what to do what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
I tried a couple more times.  The keyboard certainly is not the issue, since I'm able to edit grub every time.  And I tried a second keyboard, and had the same results.  I actually just found that if I get to that terminal and wait 15 seconds, the cursor will move from after the colon (where we'd expect it) to underneath the first char of the line.

So are you suggesting I just boot to a live cd and run a file system check/repair on the entire drive and try again?  Do you think [this]("https://help.ubuntu.com/community/LiveCdRecovery#Update_Failure") would prove beneficial at all?

Man... I am just not good at this.  I'm having trouble running fsck from the livecd... [http://i.imgur.com/pYdtMhd.jpg](http://i.imgur.com/pYdtMhd.jpg).  When I select 1 for the first prompt, it doesn't do anything.

Everything works fine when booting to the live CD - I really don't think it's BIOS related.

---

### Post by Bashing-om on 2015-12-13
andre46; Hey ..

Right now we still have no idea where the problem lies . Looking to find any hints .
We must get to a terminal by any means we can come up with.

And a fact that it is foremost in my mind to get this system updated . and IF we can and there is no other alternative then YES
I would recommend a FULL change root routine . And in this CHRoot see what the status of the system updates is.
And YES in this CHange Root environment we can complete the upgrade process .

A FULL change root might be the quickest way forward . How comfortable are you with linux and the command line ?
Ya want to do this change quick, or in easier-to-understand steps to achieve the switch from the live environment into the install ?
My change root routine is a bit more comprehensive than that given in the link you reference. And is what I have in mind.

I am here to guide and assist, but it is your system, your effort, and your thought process - how you want to handle this and proceed that is the foremost consideration.

Again, we must get to a terminal, somehow.
[INDENT][INDENT]it's linux
[INDENT][INDENT][INDENT]we can make it happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
I can run some commands, no problem.  But if any errors come up... I mean, I've only been running this server for about 8 months, and before this, I've been mostly windows.

I had tried running the procedure listed earlier, but I hit an error and quit (for fear or making a mistake) - when running step 4, I got an error that "/mnt/dev" doesn't exist.  I'm pretty sure that in step 3, I'm supposed to replace "/dev/sda1" with the path for the server hdd, which is "/media/ubuntu/e1abd730-(etc...)", but I'm really not sure...

---

### Post by Bashing-om on 2015-12-13
andre46; OK ..

Let's do this !

To run the file system check(s) AND also set up the CHange root environment, we have to identify what the targets are.

Boot the liveDVD and show us the outputs - Between code tags -> to maintain formatting and promote readability:
```

sudo fdisk -lu
sudo blkid

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Once the targets are identified we run the file system checks.
If when the file system is intact then we CHRoot into the system and do some poking about prior to updating .

That's my plan, I am open to your thoughts.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
```
Disk /dev/loop0: 628.3 MiB, 658841600 bytes, 1286800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
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

Disk /dev/zram0: 399.5 MiB, 418848768 bytes, 102258 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/zram1: 399.5 MiB, 418848768 bytes, 102258 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
```

```
/dev/sda1: UUID="51AB-2663" TYPE="vfat" PARTUUID="c712dc64-a7d7-4ad3-a5dc-e07490a705d3" 
/dev/sda2: UUID="e1abd730-7d20-4120-90d2-d71282a96d87" TYPE="ext4" PARTUUID="50cfa454-3cf7-4182-a210-e2fe1882ba4f" 
/dev/sr0: UUID="2014-10-22-19-34-32-00" LABEL="Lubuntu 14.10 amd64" TYPE="iso9660" PTUUID="16cb9898" PTTYPE="dos" 
/dev/loop0: TYPE="squashfs" 
/dev/sda3: UUID="412337ba-019b-45a7-8376-2a9236201a2e" TYPE="swap" PARTUUID="6385f4ee-8cd8-4540-9fb7-62587471f4d4" 
/dev/zram0: UUID="178eae2c-0cf9-4811-b6e5-78da6a7cb957" TYPE="swap" 
/dev/zram1: UUID="538acdf2-84ee-4145-8a39-a0527d7c64c3" TYPE="swap" 
```

---

### Post by Bashing-om on 2015-12-13
andre46; Making progress;

However:
> 
Disklabel type: gpt

we need to swap tools to deal with 'GPT' .
I do not recall if gdisk is installed by default, is it installed in the liveDVD ?
```

dpkg -l gdisk

```
Where I do have it installed:
```

sysop@1404mini:~$ dpkg -l gdisk
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name             Version       Architecture  Description
+++-================-=============-=============-=====================================
ii  gdisk            0.8.8-1ubuntu amd64         GPT fdisk text-mode partitioning tool
sysop@1404mini:~$

```

If needed install the tool:
```

sudo apt-get install gdisk

```

Now what have we to work with ?
```

sudo gdisk -l /dev/sda

``` Because 'sda' is our present target, and we want to find out what partition holds the root ( / ) file system.

[INDENT][INDENT]a bit at the time
[INDENT][INDENT][INDENT]getting there
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
ok, I installed gdisk:
```
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 625142448 sectors, 298.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): ACFD792E-2C80-4140-8521-A86C62920137
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 625142414
Partitions will be aligned on 2048-sector boundaries
Total free space is 2669 sectors (1.3 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1050623   512.0 MiB   8300  
   2         1050624       621787135   296.0 GiB   8300  
   3       621787136       625141759   1.6 GiB     8200  
```

---

### Post by Bashing-om on 2015-12-13
andre46; OK ..

We now know that sda2 is our target for the file system check :
> 
 2         1050624       621787135   296.0 GiB   8300


and we tell the file system checker to do it's thing:
```

sudo e2fsck -C0 -p -f -v /dev/sda2

```
#if errors: -y auto answers yes for fixes - because the tools is much smarter than I am -  needing response see: man e2fsck
Then do:
```

sudo e2fsck -f -y -v /dev/sda2

```

Back out of all and try and boot now into the install ... what now results ?

[INDENT][INDENT]hey
[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
Scan was quick - no errors, and it looks fine to me
```
      278898 inodes used (1.44%, out of 19398656)
        1015 non-contiguous files (0.4%)
         359 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 255047/254/1
     7892379 blocks used (10.17%, out of 77592064)
           0 bad blocks
           1 large file

      219770 regular files
       34673 directories
          57 character device files
          25 block device files
           8 fifos
          28 links
       24354 symbolic links (23496 fast symbolic links)
           2 sockets
------------
      278917 files
```

---

### Post by Bashing-om on 2015-12-13
andre46; Yeah ..

Agreed, The file system check looks clean to me too .

OK, let's do the CHRoot and prepare to update the system.

```

sudo mount /dev/sda1 /mnt/boot
sudo mount /dev/sda2 /mnt
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run

sudo chroot /mnt/ /bin/bash

```

We are now in the install as root - so exercise extra caution in what we do ! - from the liveDVD ..
Let's get some stats .
Do we have disk space ?
```

df -h
df -i

```

And what is the status of the installed kernels :
```

dpkg -l | grep linux-

```

Next time IF we are set, we do the actual updates.

When you are done here in the CHRoot -> 
Now to back out of the install and return to the live environment ( properly closing out the files on the install !) :
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt
sudo umount /mnt/boot

```

[INDENT][INDENT]ain't no step
[INDENT][INDENT][INDENT]for a stepper
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
ok, I got the chroot, and then ran the 2 df commands, as well as the dpkg command, and here is the result: ```
root@lubuntu:/# df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda2       292G   26G  252G  10% /
udev            788M  4.0K  788M   1% /dev
tmpfs           160M  1.1M  159M   1% /run
root@lubuntu:/# df -i
Filesystem       Inodes  IUsed    IFree IUse% Mounted on
/dev/sda2      19398656 278898 19119758    2% /
udev             201560    509   201051    1% /dev
tmpfs            204515    558   203957    1% /run
root@lubuntu:/# dpkg -l | grep linux-
ii  linux-firmware                                              1.143.3                                 all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.19.0.30.29                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-26                                     3.19.0-26.28                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                             3.19.0-26.28                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                                     3.19.0-28.30                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                             3.19.0-28.30                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                                     3.19.0-30.34                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                             3.19.0-30.34                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.19.0.30.29                            amd64        Generic Linux kernel headers
rc  linux-image-3.16.0-23-generic                               3.16.0-23.31                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-33-generic                               3.16.0-33.44                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-34-generic                               3.16.0-34.47                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-36-generic                               3.16.0-36.48                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-37-generic                               3.16.0-37.51                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-38-generic                               3.16.0-38.52                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-39-generic                               3.16.0-39.53                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-41-generic                               3.16.0-41.57                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-43-generic                               3.16.0-43.58                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.16.0-44-generic                               3.16.0-44.59                            amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-26-generic                               3.19.0-26.28                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                               3.19.0-28.30                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                               3.19.0-30.34                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic                               3.19.0-37.42                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic                               3.19.0-39.44                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                         3.16.0-23.31                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-33-generic                         3.16.0-33.44                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-34-generic                         3.16.0-34.47                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-36-generic                         3.16.0-36.48                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-37-generic                         3.16.0-37.51                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-38-generic                         3.16.0-38.52                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-39-generic                         3.16.0-39.53                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-41-generic                         3.16.0-41.57                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-43-generic                         3.16.0-43.58                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.16.0-44-generic                         3.16.0-44.59                            amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                         3.19.0-30.34                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.19.0.30.29                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.19.0-30.34                            amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                        3.19.0.30.29                            amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.16.0-33-generic                        3.16.0-33.44                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-34-generic                        3.16.0-34.47                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-36-generic                        3.16.0-36.48                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-37-generic                        3.16.0-37.51                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-38-generic                        3.16.0-38.52                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-39-generic                        3.16.0-39.53                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-41-generic                        3.16.0-41.57                            amd64        Signed kernel image generic
rc  linux-signed-image-3.16.0-43-generic                        3.16.0-43.58                            amd64        Signed kernel image generic
ii  linux-signed-image-3.16.0-44-generic                        3.16.0-44.59                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-26-generic                        3.19.0-26.28                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-28-generic                        3.19.0-28.30                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-30-generic                        3.19.0-30.34                            amd64        Signed kernel image generic
ii  linux-signed-image-generic                                  3.19.0.30.29                            amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-5ubuntu1                    all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu6                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

I'm a bit unclear on what comes next after your "Next time IF we are set, we do the actual updates." comment, so I just stopped and posted this - so I still have chroot.

---

### Post by Bashing-om on 2015-12-13
andre46; Great .So far so good ..

Gimme a bit to think this over .. If ya look at the kernels ... there is some kind of a mess .
Headers - image - image-extra - signed-image ; none of them agree, one to the others .. They should all match.

As a 1st step we clean all this up .. as soon as I can craft up a 'procedure' .

Hold what ya got here in the CHRoot and I be back soonest , - smoke break ! - to cogitate.

[INDENT][INDENT]seems reasonable to me
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-13
Awesome - well, you can take your time. I'll leave the system idle... I'm off to bed now, but I'll be able to follow whatever procedure you come up with tomorrow night!  Thanks so much for your help thus far!

---

### Post by Bashing-om on 2015-12-13
andre46; Well .. 

Not really as bad as IT 1st looked ... 
Reason for the booting issues is that the latest kernels ( 3.19.0-37 and -39 ) are not fully installed.

Let's take a gentle poke at this - as the related headers are not install should be safe to purge:
```

sudo dpkg -P linux-signed-image-3.16.0-44-generic 
sudo dpkg -P linux-image-extra-3.16.0-44-generic
sudo dpkg -P linux-image-3.16.0-44-generic

```

And then clean things up a bit to get a clearer picture:
```

dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```
to get the 'rc' clutter out of our way .

Then a new look:
```

dpkg -l | grep linux-

```
and we consider what it will take to fully install those latest kernels.

[INDENT][INDENT]making progress
[INDENT][INDENT][INDENT]slowly
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-14
that last command resulted in an error ```
root@lubuntu:/# dpkg - l | grep linux-
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
```

Edit - whops, I found and removed the space char.  Here's the result:```
root@lubuntu:/# dpkg -l | grep linux-
ii  linux-firmware                                              1.143.3                                 all          Firmware for Linux kernel drivers
ii  linux-generic                                               3.19.0.30.29                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-26                                     3.19.0-26.28                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-26-generic                             3.19.0-26.28                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-28                                     3.19.0-28.30                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic                             3.19.0-28.30                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30                                     3.19.0-30.34                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic                             3.19.0-30.34                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                                       3.19.0.30.29                            amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-26-generic                               3.19.0-26.28                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic                               3.19.0-28.30                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic                               3.19.0-30.34                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic                               3.19.0-37.42                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic                               3.19.0-39.44                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-26-generic                         3.19.0-26.28                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic                         3.19.0-28.30                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic                         3.19.0-30.34                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                                         3.19.0.30.29                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                        3.19.0-30.34                            amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                        3.19.0.30.29                            amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.19.0-26-generic                        3.19.0-26.28                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-28-generic                        3.19.0-28.30                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-30-generic                        3.19.0-30.34                            amd64        Signed kernel image generic
ii  linux-signed-image-generic                                  3.19.0.30.29                            amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:6.03+dfsg-5ubuntu1                    all          collection of bootloaders (common)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu6                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by Bashing-om on 2015-12-14
andre46; Yeah,

Much cleaner now, and easier to work with .
And yeah, on that added space, tired and missed that .. concerned too what else I may have missed . ( like in root and 'sudo' not required ) .

Anyway .. onward and forward !

Let's make double sure we have networking in this CHRoot:
```

ping -c3 ubuntu.com

```
Should be as :
```

sysop@1404mini:~$ ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=54 time=115 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=54 time=114 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=54 time=113 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 113.774/114.706/115.819/0.888 ms
sysop@1404mini:~$

```

what now with installing the latest kernels :
```

apt install linux-image-extra-3.19.0-39-generic 
apt install linux-signed-image-3.19.0-39-generic 
apt install linux-headers-3.19.0-39-generic
apt install linux-headers-3.19.0-39

```
I "think" I have the install order right - when this sequence runs, repeat for the -37 kernel (replace 39 with 37) .
Get us some cheap insurance that all is going well:
run:
```

update-grub

```
Paying attention here for any errors that grub reports.
Now let us look at what we have set for the booting kernel:
```

ls -al /vmlinuz*
ls -al /initrd.img*

```

Depending on what is, is what we do next .
Maybe now we can back out of the CHRoot and boot that install ... maybe

[INDENT][INDENT][INDENT]it could happen
[/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-14
Everything went fine, but I figured I should give you the log for everything we just did ```
root@lubuntu:/# ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=47 time=95.4 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=47 time=91.9 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=47 time=92.6 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 91.909/93.324/95.446/1.567 ms
root@lubuntu:/# apt install linux-image-extra-3.19.0-39-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-image-extra-3.19.0-39-generic
0 upgraded, 1 newly installed, 0 to remove and 199 not upgraded.
Need to get 0 B/38.5 MB of archives.
After this operation, 161 MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-image-extra-3.19.0-39-generic
Install these packages without verification? [y/N] y
Selecting previously unselected package linux-image-extra-3.19.0-39-generic.
(Reading database ... 196459 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.19.0-39-generic_3.19.0-39.44_amd64.deb ...
Unpacking linux-image-extra-3.19.0-39-generic (3.19.0-39.44) ...
Setting up linux-image-extra-3.19.0-39-generic (3.19.0-39.44) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
Error! Your kernel headers for kernel 3.19.0-39-generic cannot be found.
Please install the linux-headers-3.19.0-39-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@lubuntu:/# apt install linux-signed-image-3.19.0-39-generic 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-signed-image-3.19.0-39-generic
0 upgraded, 1 newly installed, 0 to remove and 199 not upgraded.
Need to get 0 B/4,050 B of archives.
After this operation, 38.9 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-signed-image-3.19.0-39-generic
Install these packages without verification? [y/N] y
Selecting previously unselected package linux-signed-image-3.19.0-39-generic.
(Reading database ... 200693 files and directories currently installed.)
Preparing to unpack .../linux-signed-image-3.19.0-39-generic_3.19.0-39.44_amd64.deb ...
Unpacking linux-signed-image-3.19.0-39-generic (3.19.0-39.44) ...
Setting up linux-signed-image-3.19.0-39-generic (3.19.0-39.44) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@lubuntu:/# apt install linux-headers-3.19.0-39-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.19.0-39
The following NEW packages will be installed:
  linux-headers-3.19.0-39 linux-headers-3.19.0-39-generic
0 upgraded, 2 newly installed, 0 to remove and 199 not upgraded.
Need to get 0 B/10.1 MB of archives.
After this operation, 80.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  linux-headers-3.19.0-39 linux-headers-3.19.0-39-generic
Install these packages without verification? [y/N] y
Selecting previously unselected package linux-headers-3.19.0-39.
(Reading database ... 200697 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.19.0-39_3.19.0-39.44_all.deb ...
Unpacking linux-headers-3.19.0-39 (3.19.0-39.44) ...
Selecting previously unselected package linux-headers-3.19.0-39-generic.
Preparing to unpack .../linux-headers-3.19.0-39-generic_3.19.0-39.44_amd64.deb ...
Unpacking linux-headers-3.19.0-39-generic (3.19.0-39.44) ...
Setting up linux-headers-3.19.0-39 (3.19.0-39.44) ...
Setting up linux-headers-3.19.0-39-generic (3.19.0-39.44) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
root@lubuntu:/# apt install linux-headers-3.19.0-39
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.19.0-39 is already the newest version.
linux-headers-3.19.0-39 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 199 not upgraded.
root@lubuntu:/# apt install linux-image-extra-3.19.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-image-extra-3.19.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 199 not upgraded.
Need to get 0 B/38.5 MB of archives.
After this operation, 161 MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-image-extra-3.19.0-37-generic
Install these packages without verification? [y/N] y
Selecting previously unselected package linux-image-extra-3.19.0-37-generic.
(Reading database ... 225657 files and directories currently installed.)
Preparing to unpack .../linux-image-extra-3.19.0-37-generic_3.19.0-37.42_amd64.deb ...
Unpacking linux-image-extra-3.19.0-37-generic (3.19.0-37.42) ...
Setting up linux-image-extra-3.19.0-37-generic (3.19.0-37.42) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
Error! Your kernel headers for kernel 3.19.0-37-generic cannot be found.
Please install the linux-headers-3.19.0-37-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-37-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@lubuntu:/# apt install linux-signed-image-3.19.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  linux-signed-image-3.19.0-37-generic
0 upgraded, 1 newly installed, 0 to remove and 199 not upgraded.
Need to get 0 B/4,062 B of archives.
After this operation, 38.9 kB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  linux-signed-image-3.19.0-37-generic
Install these packages without verification? [y/N] y
Selecting previously unselected package linux-signed-image-3.19.0-37-generic.
(Reading database ... 229891 files and directories currently installed.)
Preparing to unpack .../linux-signed-image-3.19.0-37-generic_3.19.0-37.42_amd64.deb ...
Unpacking linux-signed-image-3.19.0-37-generic (3.19.0-37.42) ...
Setting up linux-signed-image-3.19.0-37-generic (3.19.0-37.42) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
root@lubuntu:/# apt install linux-headers-3.19.0-37-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-headers-3.19.0-37
The following NEW packages will be installed:
  linux-headers-3.19.0-37 linux-headers-3.19.0-37-generic
0 upgraded, 2 newly installed, 0 to remove and 199 not upgraded.
Need to get 0 B/10.1 MB of archives.
After this operation, 80.5 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
WARNING: The following packages cannot be authenticated!
  linux-headers-3.19.0-37 linux-headers-3.19.0-37-generic
Install these packages without verification? [y/N] y
Selecting previously unselected package linux-headers-3.19.0-37.
(Reading database ... 229895 files and directories currently installed.)
Preparing to unpack .../linux-headers-3.19.0-37_3.19.0-37.42_all.deb ...
Unpacking linux-headers-3.19.0-37 (3.19.0-37.42) ...
Selecting previously unselected package linux-headers-3.19.0-37-generic.
Preparing to unpack .../linux-headers-3.19.0-37-generic_3.19.0-37.42_amd64.deb ...
Unpacking linux-headers-3.19.0-37-generic (3.19.0-37.42) ...
Setting up linux-headers-3.19.0-37 (3.19.0-37.42) ...
Setting up linux-headers-3.19.0-37-generic (3.19.0-37.42) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-37-generic /boot/vmlinuz-3.19.0-37-generic
root@lubuntu:/# apt install linux-headers-3.19.0-37
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-3.19.0-37 is already the newest version.
linux-headers-3.19.0-37 set to manually installed.
The following packages were automatically installed and are no longer required:
  linux-headers-3.19.0-26 linux-headers-3.19.0-26-generic
  linux-image-3.19.0-26-generic linux-image-extra-3.19.0-26-generic
  linux-signed-image-3.19.0-26-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 199 not upgraded.
root@lubuntu:/# update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Found linux image: /boot/vmlinuz-3.19.0-26-generic
Found initrd image: /boot/initrd.img-3.19.0-26-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
```

and here is the stuff you actually wanted to see
```
root@lubuntu:/# ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Dec 10 19:54 /vmlinuz -> boot/vmlinuz-3.19.0-39-generic
lrwxrwxrwx 1 root root 30 Dec 10 19:53 /vmlinuz.old -> boot/vmlinuz-3.19.0-37-generic
root@lubuntu:/# ls -al /initrd.img*
lrwxrwxrwx 1 root root 33 Dec 10 19:54 /initrd.img -> boot/initrd.img-3.19.0-39-generic
lrwxrwxrwx 1 root root 33 Dec 10 19:53 /initrd.img.old -> boot/initrd.img-3.19.0-37-generic
```

---

### Post by Bashing-om on 2015-12-14
andre46; Hey !

Look'n good ... bet it boots now !
Ya wanna try and see ? 

Or maybe update/upgrade the system in this CHRoot environment now ? rather than in the install ?

Pending to properly back put of the CHRoot .

What are your thoughts ?

[INDENT][INDENT]we CAN do that
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-14
Wow - I could kiss you right now!

We're back in, so I have my files back online and I can stay out of the basement with the magic of VNC, but the system errors persist: [http://i.imgur.com/A6tqlgZ.png](http://i.imgur.com/A6tqlgZ.png)

should I just run an apt-get update?

---

### Post by Bashing-om on 2015-12-14
Agoandre46; Welp:

Are you now out of the CHange Root  routine ? Did you back out 'gracefully' ?

And YES we do update/upgrade at this point seeing what the package manager thinks about the system as a whole .

[INDENT][INDENT]we are getting there 
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-14
Yes, I did back out gracefully with a chroot exit, and then umounting each path.

I ran an update/upgrade, and everything appeared to run fine.  I'm not really sure what else to do at this point...?  Celebrate?

---

### Post by Bashing-om on 2015-12-14
andre46; Well ..

Show me :
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install
sudo dpkg -C

```
And I will render back an opinion .

[INDENT][INDENT]only as good
[INDENT][INDENT][INDENT]as the tools we work with
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-14
hm... maybe not as good as I thought:
```
andre@NAS:~$ sudo apt update[sudo] password for andre: 
Hit http://us.archive.ubuntu.com vivid InRelease
Get:1 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]           
Get:2 http://security.ubuntu.com vivid-security InRelease [64.4 kB]            
Ign http://download.opensuse.org  InRelease                                    
Hit http://us.archive.ubuntu.com vivid-backports InRelease
Hit http://download.opensuse.org  Release.gpg     
Hit http://us.archive.ubuntu.com vivid/main Sources                        
Hit http://download.opensuse.org  Release                                  
Get:3 http://security.ubuntu.com vivid-security/main Sources [54.1 kB]
Hit http://us.archive.ubuntu.com vivid/restricted Sources                      
Hit http://us.archive.ubuntu.com vivid/universe Sources                        
Hit http://us.archive.ubuntu.com vivid/multiverse Sources                      
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages                     
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages          
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/main i386 Packages               
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages                
Get:4 http://security.ubuntu.com vivid-security/restricted Sources [3,418 B]   
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Get:5 http://security.ubuntu.com vivid-security/universe Sources [21.5 kB]     
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Get:6 http://security.ubuntu.com vivid-security/multiverse Sources [1,940 B]   
Hit http://us.archive.ubuntu.com vivid/main Translation-en                     
Get:7 http://security.ubuntu.com vivid-security/main amd64 Packages [167 kB]   
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en               
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                 
Get:8 http://security.ubuntu.com vivid-security/restricted amd64 Packages [11.2 kB]
Get:9 http://us.archive.ubuntu.com vivid-updates/main Sources [108 kB]         
Get:10 http://security.ubuntu.com vivid-security/universe amd64 Packages [67.6 kB]
Get:11 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [6,040 B]
Get:12 http://security.ubuntu.com vivid-security/main i386 Packages [165 kB]   
Get:13 http://us.archive.ubuntu.com vivid-updates/restricted Sources [4,351 B] 
Get:14 http://us.archive.ubuntu.com vivid-updates/universe Sources [48.4 kB]   
Get:15 http://us.archive.ubuntu.com vivid-updates/multiverse Sources [1,940 B] 
Hit http://download.opensuse.org  Packages                                     
Get:16 http://us.archive.ubuntu.com vivid-updates/main amd64 Packages [260 kB] 
Get:17 http://security.ubuntu.com vivid-security/restricted i386 Packages [10.9 kB]
Get:18 http://security.ubuntu.com vivid-security/universe i386 Packages [67.6 kB]
Get:19 http://security.ubuntu.com vivid-security/multiverse i386 Packages [6,224 B]
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en        
Get:20 http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.6 kB]
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Get:21 http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages [128 kB]
Hit http://security.ubuntu.com vivid-security/universe Translation-en          
Get:22 http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [6,040 B]
Get:23 http://us.archive.ubuntu.com vivid-updates/main i386 Packages [258 kB]  
Get:24 http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages [13.3 kB]
Get:25 http://us.archive.ubuntu.com vivid-updates/universe i386 Packages [129 kB]
Get:26 http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages [6,224 B]
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en             
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en       
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en         
Hit http://us.archive.ubuntu.com vivid-backports/main Sources       
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources 
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources   
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages           
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en       
Ign http://download.opensuse.org  Translation-en_US                            
Ign http://download.opensuse.org  Translation-en                
Fetched 1,688 kB in 22s (73.7 kB/s)                                            
Reading package lists... Done
Building dependency tree       
Reading state information... Done
141 packages can be upgraded. Run 'apt list --upgradable' to see them.
andre@NAS:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... The following packages were automatically installed and are no longer required:
  libembymagickcore-6.q8-2 libembymagickwand-6.q8-2
Use 'apt-get autoremove' to remove them.
Done
The following NEW packages will be installed:
  libembymagickcore-6.q8-2 libembymagickwand-6.q8-2
  libmono-smdiagnostics0.0-cil libmono-system-servicemodel-internals0.0-cil
The following packages have been kept back:
  emby-server
The following packages will be upgraded:
  libmono-2.0-dev libmono-accessibility4.0-cil libmono-c5-1.1-cil
  libmono-cairo4.0-cil libmono-cecil-private-cil libmono-cil-dev
  libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil
  libmono-corlib4.5-cil libmono-cscompmgd0.0-cil libmono-csharp4.0c-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft4.0a-cil libmono-http4.0-cil libmono-i18n-cjk4.0-cil
  libmono-i18n-mideast4.0-cil libmono-i18n-other4.0-cil
  libmono-i18n-rare4.0-cil libmono-i18n-west4.0-cil libmono-i18n4.0-all
  libmono-i18n4.0-cil libmono-ldap4.0-cil libmono-management4.0-cil
  libmono-messaging-rabbitmq4.0-cil libmono-messaging4.0-cil
  libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build4.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-oracle4.0-cil
  libmono-parallel4.0-cil libmono-peapi4.0a-cil libmono-posix4.0-cil
  libmono-rabbitmq4.0-cil libmono-relaxng4.0-cil libmono-security4.0-cil
  libmono-sharpzip4.84-cil libmono-simd4.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil
  libmono-system-data-entity4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil
  libmono-system-io-compression-filesystem4.0-cil
  libmono-system-io-compression4.0-cil libmono-system-json-microsoft4.0-cil
  libmono-system-json4.0-cil libmono-system-ldap-protocols4.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net-http-formatting4.0-cil
  libmono-system-net-http-webrequest4.0-cil libmono-system-net-http4.0-cil
  libmono-system-net4.0-cil libmono-system-numerics4.0-cil
  libmono-system-reactive-core2.2-cil libmono-system-reactive-debugger2.2-cil
  libmono-system-reactive-experimental2.2-cil
  libmono-system-reactive-interfaces2.2-cil
  libmono-system-reactive-linq2.2-cil
  libmono-system-reactive-observable-aliases0.0-cil
  libmono-system-reactive-platformservices2.2-cil
  libmono-system-reactive-providers2.2-cil
  libmono-system-reactive-runtime-remoting2.2-cil
  libmono-system-reactive-windows-forms2.2-cil
  libmono-system-reactive-windows-threading2.2-cil
  libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime4.0-cil
  libmono-system-security4.0-cil libmono-system-servicemodel-activation4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil
  libmono-system-serviceprocess4.0-cil
  libmono-system-threading-tasks-dataflow4.0-cil
  libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-http-selfhost4.0-cil
  libmono-system-web-http-webhost4.0-cil libmono-system-web-http4.0-cil
  libmono-system-web-mvc3.0-cil libmono-system-web-razor2.0-cil
  libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
  libmono-system-web-webpages-deployment2.0-cil
  libmono-system-web-webpages-razor2.0-cil libmono-system-web-webpages2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0a-cil
  libmono-system-windows-forms4.0-cil libmono-system-windows4.0-cil
  libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml-serialization4.0-cil libmono-system-xml4.0-cil
  libmono-system4.0-cil libmono-tasklets4.0-cil libmono-webbrowser4.0-cil
  libmono-webmatrix-data4.0-cil libmono-windowsbase4.0-cil
  libmono-xbuild-tasks4.0-cil libmonoboehm-2.0-1 libmonoboehm-2.0-dev
  mono-4.0-gac mono-devel mono-gac mono-mcs mono-runtime mono-runtime-common
  mono-runtime-sgen mono-xbuild
140 upgraded, 4 newly installed, 0 to remove and 1 not upgraded.
Need to get 0 B/28.6 MB of archives.
After this operation, 11.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
(Reading database ... 224680 files and directories currently installed.)
Preparing to unpack .../libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb ...
Unpacking libembymagickcore-6.q8-2:amd64 (8:6.9.2-8) ...
dpkg: error processing archive /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickCore-6.Q8.so.2.0.0', which is also in package libmagickcore-6.q8-2:amd64 8:6.9.1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb ...
Unpacking libembymagickwand-6.q8-2:amd64 (8:6.9.2-8) ...
dpkg: error processing archive /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8.so.2.0.0', which is also in package libmagickwand-6.q8-2:amd64 8:6.9.1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../mono-devel_4.2.1.102-0xamarin1_all.deb ...
Unpacking mono-devel (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-cil-dev_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-cil-dev (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-security4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-security4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-xml4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-xml4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-security4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-security4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-configuration4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-configuration4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-posix4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-posix4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-core4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-core4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-csharp4.0c-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-csharp4.0c-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-csharp4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-csharp4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-mcs_4.2.1.102-0xamarin1_all.deb ...
Unpacking mono-mcs (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-corlib4.5-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-corlib4.5-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-accessibility4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-accessibility4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-c5-1.1-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-c5-1.1-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-cairo4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-cairo4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-debugger-soft4.0a-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-debugger-soft4.0a-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-codecontracts4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-codecontracts4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-cecil-private-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-cecil-private-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-compilerservices-symbolwriter4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-compilerservices-symbolwriter4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-cscompmgd0.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-cscompmgd0.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-custommarshalers4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-custommarshalers4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-data-tds4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-data-tds4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-transactions4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-transactions4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-enterpriseservices4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-enterpriseservices4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-numerics4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-numerics4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-data4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-data4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-db2-1.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-db2-1.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-sharpzip4.84-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-sharpzip4.84-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-sqlite4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-sqlite4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-componentmodel-dataannotations4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-componentmodel-dataannotations4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-drawing4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-drawing4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-runtime-serialization-formatters-soap4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-runtime-serialization-formatters-soap4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-applicationservices4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-applicationservices4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-webbrowser4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-webbrowser4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n4.0-all_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n4.0-all (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n-cjk4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n-cjk4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n-mideast4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n-mideast4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n-other4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n-other4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n-rare4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n-rare4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-i18n-west4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-i18n-west4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-windows-forms4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-windows-forms4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-design4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-design4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-ldap4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-ldap4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-ldap4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-ldap4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-services4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-services4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-http4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-http4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-management4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-management4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-messaging4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-messaging4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-rabbitmq4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-rabbitmq4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-messaging-rabbitmq4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-messaging-rabbitmq4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-build-framework4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-build-framework4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-build4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-build4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-build-utilities-v4.0-4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-build-utilities-v4.0-4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-build-engine4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-build-engine4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-xbuild-tasks4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-xbuild-tasks4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-build-tasks-v4.0-4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-build-tasks-v4.0-4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-visualc10.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-visualc10.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-microsoft-web-infrastructure1.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-microsoft-web-infrastructure1.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-oracle4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-oracle4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-parallel4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-parallel4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-peapi4.0a-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-peapi4.0a-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-relaxng4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-relaxng4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-simd4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-simd4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Selecting previously unselected package libmono-system-servicemodel-internals0.0-cil.
Preparing to unpack .../libmono-system-servicemodel-internals0.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-servicemodel-internals0.0-cil (4.2.1.102-0xamarin1) ...
Selecting previously unselected package libmono-smdiagnostics0.0-cil.
Preparing to unpack .../libmono-smdiagnostics0.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-smdiagnostics0.0-cil (4.2.1.102-0xamarin1) ...
Preparing to unpack .../libmono-system-componentmodel-composition4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-componentmodel-composition4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-configuration-install4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-configuration-install4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-data-datasetextensions4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-data-datasetextensions4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-runtime-serialization4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-runtime-serialization4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-xml-linq4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-xml-linq4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-data-entity4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-data-entity4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-data-linq4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-data-linq4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-data-services-client4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-data-services-client4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-identitymodel4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-identitymodel4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-identitymodel-selectors4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-identitymodel-selectors4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-messaging4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-messaging4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-servicemodel4.0a-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-servicemodel4.0a-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-servicemodel-activation4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-servicemodel-activation4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-extensions4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-extensions4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-servicemodel-web4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-servicemodel-web4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-data-services4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-data-services4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-drawing-design4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-drawing-design4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-dynamic4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-dynamic4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-io-compression4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-io-compression4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-io-compression-filesystem4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-io-compression-filesystem4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-json4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-json4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-json-microsoft4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-json-microsoft4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-ldap-protocols4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-ldap-protocols4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-management4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-management4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-net4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-net4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-net-http4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-net-http4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-net-http-formatting4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-net-http-formatting4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-net-http-webrequest4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-net-http-webrequest4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-interfaces2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-interfaces2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-core2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-core2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-linq2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-linq2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-debugger2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-debugger2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-experimental2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-experimental2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-providers2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-providers2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-observable-aliases0.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-observable-aliases0.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-platformservices2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-platformservices2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-runtime-remoting2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-runtime-remoting2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-windows-forms2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-windows-forms2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-xaml4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-xaml4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-windowsbase4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-windowsbase4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-reactive-windows-threading2.2-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-reactive-windows-threading2.2-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-runtime4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-runtime4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-runtime-caching4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-runtime-caching4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-runtime-durableinstancing4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-runtime-durableinstancing4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-servicemodel-discovery4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-servicemodel-discovery4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-servicemodel-routing4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-servicemodel-routing4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-serviceprocess4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-serviceprocess4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-threading-tasks-dataflow4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-threading-tasks-dataflow4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-abstractions4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-abstractions4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-dynamicdata4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-dynamicdata4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-extensions-design4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-extensions-design4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-http4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-http4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-http-selfhost4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-http-selfhost4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-http-webhost4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-http-webhost4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-razor2.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-razor2.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-webpages-deployment2.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-webpages-deployment2.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-webpages2.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-webpages2.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-webpages-razor2.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-webpages-razor2.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-mvc3.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-mvc3.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-web-routing4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-web-routing4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-windows4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-windows4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-windows-forms-datavisualization4.0a-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-windows-forms-datavisualization4.0a-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-system-xml-serialization4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-system-xml-serialization4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-webmatrix-data4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-webmatrix-data4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-tasklets4.0-cil_4.2.1.102-0xamarin1_all.deb ...
Unpacking libmono-tasklets4.0-cil (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-runtime_4.2.1.102-0xamarin1_amd64.deb ...
Unpacking mono-runtime (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-runtime-sgen_4.2.1.102-0xamarin1_amd64.deb ...
Unpacking mono-runtime-sgen (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-runtime-common_4.2.1.102-0xamarin1_amd64.deb ...
Unpacking mono-runtime-common (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-gac_4.2.1.102-0xamarin1_all.deb ...
Unpacking mono-gac (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-4.0-gac_4.2.1.102-0xamarin1_all.deb ...
Unpacking mono-4.0-gac (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../mono-xbuild_4.2.1.102-0xamarin1_all.deb ...
Unpacking mono-xbuild (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmono-2.0-dev_4.2.1.102-0xamarin1_amd64.deb ...
Unpacking libmono-2.0-dev (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmonoboehm-2.0-dev_4.2.1.102-0xamarin1_amd64.deb ...
Unpacking libmonoboehm-2.0-dev (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Preparing to unpack .../libmonoboehm-2.0-1_4.2.1.102-0xamarin1_amd64.deb ...
Unpacking libmonoboehm-2.0-1 (4.2.1.102-0xamarin1) over (4.0.3.20-0xamarin1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb
 /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
andre@NAS:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
142 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up libmonoboehm-2.0-1 (4.2.1.102-0xamarin1) ...
Setting up libmonoboehm-2.0-dev (4.2.1.102-0xamarin1) ...
Setting up libmono-2.0-dev (4.2.1.102-0xamarin1) ...
Setting up mono-4.0-gac (4.2.1.102-0xamarin1) ...
Setting up mono-gac (4.2.1.102-0xamarin1) ...
* Installing 1 assembly from libnunit-console-runner2.6.3-cil into Mono
* Installing 1 assembly from libnunit-core2.6.3-cil into Mono
* Installing 1 assembly from libnunit-core-interfaces2.6.3-cil into Mono
* Installing 1 assembly from libnunit-framework2.6.3-cil into Mono
* Installing 1 assembly from libnunit-mocks2.6.3-cil into Mono
* Installing 1 assembly from libnunit-util2.6.3-cil into Mono
Setting up mono-runtime-common (4.2.1.102-0xamarin1) ...
Installing new version of config file /etc/mono/4.5/machine.config ...
Setting up mono-runtime-sgen (4.2.1.102-0xamarin1) ...
Setting up mono-runtime (4.2.1.102-0xamarin1) ...
Setting up libmono-corlib4.5-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-accessibility4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-cecil-private-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-build-framework4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-peapi4.0a-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-numerics4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n-west4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-c5-1.1-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-cairo4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-custommarshalers4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n-cjk4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n-mideast4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n-other4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n-rare4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-i18n4.0-all (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-visualc10.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-parallel4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-simd4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-tasklets4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-security4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-xml4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-runtime-serialization-formatters-soap4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-security4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-configuration4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-posix4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-core4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-codecontracts4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-compilerservices-symbolwriter4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-csharp4.0c-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-data-tds4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-ldap4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-messaging4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-build-utilities-v4.0-4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-build-engine4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-rabbitmq4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-relaxng4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-sharpzip4.84-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-transactions4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-enterpriseservices4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-data4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-sqlite4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-componentmodel-composition4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-componentmodel-dataannotations4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-configuration-install4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-servicemodel-internals0.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-runtime-serialization4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-data-linq4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-xml-linq4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-data-services-client4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-drawing4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-applicationservices4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-ldap4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-webbrowser4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-windows-forms4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-design4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-services4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-identitymodel4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-identitymodel-selectors4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-messaging4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-runtime4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-servicemodel4.0a-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-extensions4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-xaml4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-xbuild-tasks4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-csharp4.0-cil (4.2.1.102-0xamarin1) ...
Setting up mono-mcs (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-build-tasks-v4.0-4.0-cil (4.2.1.102-0xamarin1) ...
Setting up mono-xbuild (4.2.1.102-0xamarin1) ...
Setting up libmono-cscompmgd0.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-db2-1.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-debugger-soft4.0a-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-http4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-management4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-messaging-rabbitmq4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-build4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-microsoft-web-infrastructure1.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-oracle4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-smdiagnostics0.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-data-datasetextensions4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-data-entity4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-drawing-design4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-dynamic4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-io-compression4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-io-compression-filesystem4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-json4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-json-microsoft4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-ldap-protocols4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-management4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-net4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-net-http4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-net-http-formatting4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-net-http-webrequest4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-interfaces2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-core2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-linq2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-debugger2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-experimental2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-providers2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-observable-aliases0.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-platformservices2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-runtime-remoting2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-windows-forms2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-windowsbase4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-reactive-windows-threading2.2-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-runtime-caching4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-runtime-durableinstancing4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-servicemodel-discovery4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-servicemodel-routing4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-serviceprocess4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-threading-tasks-dataflow4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-abstractions4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-dynamicdata4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-extensions-design4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-http4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-http-selfhost4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-http-webhost4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-razor2.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-webpages-deployment2.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-webpages2.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-webpages-razor2.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-mvc3.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-web-routing4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-windows4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-windows-forms-datavisualization4.0a-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-xml-serialization4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-webmatrix-data4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-servicemodel-activation4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-servicemodel-web4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-system-data-services4.0-cil (4.2.1.102-0xamarin1) ...
Setting up libmono-cil-dev (4.2.1.102-0xamarin1) ...
Setting up mono-devel (4.2.1.102-0xamarin1) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
andre@NAS:~$ sudo dpkg -C
andre@NAS:~$ 
```

---

### Post by Bashing-om on 2015-12-14
andre46; Hummm ...

OK .. where did you get " emby-server " , as I can not readily find it ?

Ouch !!! Mixing distribution repositories is a sure road to disaster:
> 
Hit [http://download.opensuse.org](http://download.opensuse.org)  Packages

Let's take a look at what you have been doing.
show us :
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```
And as we do have a version conflict :
what returns:
```

apt-cache policy libembymagickcore-6.q8

```
as we start the process to identify a package I have yet to be able to identify !

[INDENT][INDENT]Oh BoY
[INDENT][INDENT][INDENT][INDENT]we may now have our work cut out for us
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-14
[Emby ]("http://kodi.wiki/view/Add-on:Emby_for_Kodi")is a Kodi add-on that runs server-side.  I installed it, never used it, and decided it wasn't really what I wanted, so I'm ok with wiping all traces of it.
```
andre@NAS:~$ cat -n /etc/apt/sources.list     1	# deb cdrom:[Lubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main multiverse restricted universe
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     6	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    11	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ vivid universe
    17	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    19	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    27	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    29	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    37	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu vivid-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
    41	deb http://security.ubuntu.com/ubuntu vivid-security universe
    42	deb-src http://security.ubuntu.com/ubuntu vivid-security universe
    43	deb http://security.ubuntu.com/ubuntu vivid-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu utopic partner
    51	# deb-src http://archive.canonical.com/ubuntu utopic partner
    52	
andre@NAS:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/emby-server.list <==
deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/ /


==> /etc/apt/sources.list.d/modriscoll-ubuntu-nzbget-utopic.list <==
# deb http://ppa.launchpad.net/modriscoll/nzbget/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/modriscoll/nzbget/ubuntu utopic main


==> /etc/apt/sources.list.d/modriscoll-ubuntu-nzbget-utopic.list.distUpgrade <==
deb http://ppa.launchpad.net/modriscoll/nzbget/ubuntu utopic main
# deb-src http://ppa.launchpad.net/modriscoll/nzbget/ubuntu utopic main


==> /etc/apt/sources.list.d/nodesource.list <==
# deb https://deb.nodesource.com/node_0.12 vivid main # disabled on upgrade to vivid
# deb-src https://deb.nodesource.com/node_0.12 vivid main # disabled on upgrade to vivid


==> /etc/apt/sources.list.d/nodesource.list.distUpgrade <==
deb https://deb.nodesource.com/node_0.12 utopic main
deb-src https://deb.nodesource.com/node_0.12 utopic main


==> /etc/apt/sources.list.d/sonarr.list <==
# deb http://apt.sonarr.tv/ master main # disabled on upgrade to vivid


==> /etc/apt/sources.list.d/sonarr.list.distUpgrade <==
deb http://apt.sonarr.tv/ master main
andre@NAS:~$ apt-cache policy libembymagickcore-6.q8
libembymagickcore-6.q8-2:
  Installed: (none)
  Candidate: 8:6.9.2-8
  Version table:
     8:6.9.2-8 0
        500 http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/  Packages
```

---

### Post by Bashing-om on 2015-12-14
andre46; Welp;

Does not look as bad as I had feared .
" [http://download.opensuse.org](http://download.opensuse.org) " appears to be xubuntu based, so it's presence should not hurt.
But I agree, if one does not use it, get rid of it !

As to the how .. right now I do not know enough to say. It is late here now for me .. I start this again on my morrow after my chores are done.

In the meantime I do suggest and recommend that the " vivid-backports" repository be disabled . In a stable system one gets what one wants from this repo and then turn it back off . There is and can be and most likely is version conflicts with the installed system files and libraries.
We cross that bridge when we have emby removed .

still treading water
[INDENT][INDENT][INDENT]sharks ain't got us yet
[/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-12-15
andre46; Morning ...

OK all indications are that the package manager is able to track emby-server. Let's try this:
```

sudo apt-get --purge remove emby-server

```
Paying attention to what gets broke, and what we need to replace .

Now we want to know if anything else is left on the system:
what returns:
```

dpkg -l | grep emby

```

And left to do is to remove the fetch from the sources.list.d directory .
And a bit of final cleanup .. 'autoremove' to remove the/any orphaned files.

Once these are done, and the backport is turned off .. see now what update/upgrade results in.

[INDENT][INDENT]maybe
[INDENT][INDENT][INDENT]as easy as falling out of bed wide-awake
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-12-17
andre46; Hey ....

What condition is our condition in ?

Do you now have the package manager all squared away ?

[INDENT][INDENT]not done
[INDENT][INDENT][INDENT]'til it is all done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-17
yes, very sorry for the delay - I had a couple days where I wasn't home at all.  Since I have VNC locked down to only my home network, this had to sit for a bit.  That first command resulted in at least one error:```
andre@NAS:~$ sudo apt-get --purge remove emby-server[sudo] password for andre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libart-2.0-2 libbonoboui2-0 libbonoboui2-common libgail18 libgdiplus
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libmono-2.0-dev libmono-accessibility4.0-cil libmono-c5-1.1-cil
  libmono-cairo4.0-cil libmono-cecil-private-cil libmono-cil-dev
  libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil
  libmono-cscompmgd0.0-cil libmono-csharp4.0c-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft4.0a-cil libmono-http4.0-cil libmono-ldap4.0-cil
  libmono-management4.0-cil libmono-messaging-rabbitmq4.0-cil
  libmono-messaging4.0-cil libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build4.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-oracle4.0-cil
  libmono-parallel4.0-cil libmono-peapi4.0a-cil libmono-posix4.0-cil
  libmono-rabbitmq4.0-cil libmono-relaxng4.0-cil libmono-sharpzip4.84-cil
  libmono-simd4.0-cil libmono-smdiagnostics0.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil
  libmono-system-data-entity4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil
  libmono-system-io-compression-filesystem4.0-cil
  libmono-system-io-compression4.0-cil libmono-system-json-microsoft4.0-cil
  libmono-system-json4.0-cil libmono-system-ldap-protocols4.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net-http-formatting4.0-cil
  libmono-system-net-http-webrequest4.0-cil libmono-system-net-http4.0-cil
  libmono-system-net4.0-cil libmono-system-numerics4.0-cil
  libmono-system-reactive-core2.2-cil libmono-system-reactive-debugger2.2-cil
  libmono-system-reactive-experimental2.2-cil
  libmono-system-reactive-interfaces2.2-cil
  libmono-system-reactive-linq2.2-cil
  libmono-system-reactive-observable-aliases0.0-cil
  libmono-system-reactive-platformservices2.2-cil
  libmono-system-reactive-providers2.2-cil
  libmono-system-reactive-runtime-remoting2.2-cil
  libmono-system-reactive-windows-forms2.2-cil
  libmono-system-reactive-windows-threading2.2-cil
  libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime4.0-cil
  libmono-system-servicemodel-activation4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-internals0.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil
  libmono-system-serviceprocess4.0-cil
  libmono-system-threading-tasks-dataflow4.0-cil
  libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-http-selfhost4.0-cil
  libmono-system-web-http-webhost4.0-cil libmono-system-web-http4.0-cil
  libmono-system-web-mvc3.0-cil libmono-system-web-razor2.0-cil
  libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
  libmono-system-web-webpages-deployment2.0-cil
  libmono-system-web-webpages-razor2.0-cil libmono-system-web-webpages2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0a-cil
  libmono-system-windows-forms4.0-cil libmono-system-windows4.0-cil
  libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml-serialization4.0-cil libmono-tasklets4.0-cil
  libmono-webbrowser4.0-cil libmono-webmatrix-data4.0-cil
  libmono-windowsbase4.0-cil libmono-xbuild-tasks4.0-cil libmonoboehm-2.0-1
  libmonoboehm-2.0-dev libnunit-cil-dev libnunit-console-runner2.6.3-cil
  libnunit-core-interfaces2.6.3-cil libnunit-core2.6.3-cil
  libnunit-framework2.6.3-cil libnunit-mocks2.6.3-cil libnunit-util2.6.3-cil
  mono-csharp-shell mono-devel mono-mcs mono-xbuild
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  emby-server*
0 upgraded, 0 newly installed, 1 to remove and 32 not upgraded.
After this operation, 48.0 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 224694 files and directories currently installed.)
Removing emby-server (3.0.5724.6) ...
/var/lib/dpkg/info/emby-server.prerm: 23: [: missing ]
/var/lib/dpkg/info/emby-server.prerm: 23: [: missing ]
Purging configuration files for emby-server (3.0.5724.6) ...
/var/lib/dpkg/info/emby-server.postrm: 41: [: missing ]
dpkg: error processing package emby-server (--purge):
 subprocess installed post-removal script returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
Looks like it's being stubborn...
```
andre@NAS:~$ dpkg -l | grep emby
pc  emby-server                                                 3.0.5724.6                              all          Emby Server is a home media server.
```

---

### Post by Bashing-om on 2015-12-17
andre46; Ouch !

That is a blow, not having the packaging  scripts . Presently I do no know of a good way around this limitation.

Maybe we will have to install emby-server - before we can now do the removal ???

[INDENT][INDENT]ponder for
[INDENT][INDENT][INDENT]a better alternative
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-17
whatever you want to try, I'm on board!

I followed the instructions [here]("https://emby.media/downloads/linux-server/") to try to install emby again.  Doesn't seem like it worked quite right...
```
andre@NAS:~$ wget -qO - http://download.opensuse.org/repositories/home:emby/xUbuntu_15.04/Release.key | sudo apt-key add -[sudo] password for andre: 
OK
andre@NAS:~$ sudo sh -c "echo 'deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/ /' >> /etc/apt/sources.list.d/emby-server.list"
andre@NAS:~$ sudo apt-get update
Get:1 http://security.ubuntu.com vivid-security InRelease [64.4 kB]
Ign http://download.opensuse.org  InRelease                                    
Hit http://us.archive.ubuntu.com vivid InRelease                               
Get:2 http://us.archive.ubuntu.com vivid-updates InRelease [64.4 kB]
Hit http://us.archive.ubuntu.com vivid-backports InRelease
Get:3 http://download.opensuse.org  Release.gpg [481 B]
Get:4 http://download.opensuse.org  Release [1,009 B]
Get:5 http://security.ubuntu.com vivid-security/main Sources [55.7 kB]
Get:6 http://security.ubuntu.com vivid-security/restricted Sources [3,418 B]
Get:7 http://security.ubuntu.com vivid-security/universe Sources [22.2 kB]
Get:8 http://security.ubuntu.com vivid-security/multiverse Sources [1,940 B]   
Get:9 http://security.ubuntu.com vivid-security/main amd64 Packages [173 kB]
Get:10 http://security.ubuntu.com vivid-security/restricted amd64 Packages [11.2 kB]
Get:11 http://security.ubuntu.com vivid-security/universe amd64 Packages [71.5 kB]
Get:12 http://security.ubuntu.com vivid-security/multiverse amd64 Packages [6,040 B]
Get:13 http://security.ubuntu.com vivid-security/main i386 Packages [171 kB]   
Get:14 http://security.ubuntu.com vivid-security/restricted i386 Packages [10.9 kB]
Get:15 http://security.ubuntu.com vivid-security/universe i386 Packages [71.5 kB]
Get:16 http://security.ubuntu.com vivid-security/multiverse i386 Packages [6,224 B]
Get:17 http://security.ubuntu.com vivid-security/main Translation-en [83.7 kB] 
Hit http://us.archive.ubuntu.com vivid/main Sources                            
Hit http://us.archive.ubuntu.com vivid/restricted Sources                      
Hit http://us.archive.ubuntu.com vivid/universe Sources                 
Hit http://us.archive.ubuntu.com vivid/multiverse Sources               
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages              
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages          
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/main i386 Packages               
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages         
Get:18 http://security.ubuntu.com vivid-security/multiverse Translation-en [2,743 B]
Get:19 http://security.ubuntu.com vivid-security/restricted Translation-en [2,774 B]
Get:20 http://security.ubuntu.com vivid-security/universe Translation-en [45.0 kB]
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://us.archive.ubuntu.com vivid/main Translation-en                     
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en               
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en               
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                 
Get:21 http://us.archive.ubuntu.com vivid-updates/main Sources [109 kB]        
Get:22 http://us.archive.ubuntu.com vivid-updates/restricted Sources [4,351 B] 
Get:23 http://us.archive.ubuntu.com vivid-updates/universe Sources [49.1 kB]   
Get:24 http://us.archive.ubuntu.com vivid-updates/multiverse Sources [1,940 B] 
Get:25 http://us.archive.ubuntu.com vivid-updates/main amd64 Packages [264 kB] 
Get:26 http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages [13.6 kB]
Get:27 http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages [132 kB]
Get:28 http://download.opensuse.org  Packages [64.4 kB]                        
Get:29 http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages [6,040 B]
Get:30 http://us.archive.ubuntu.com vivid-updates/main i386 Packages [261 kB]  
Get:31 http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages [13.3 kB]
Get:32 http://us.archive.ubuntu.com vivid-updates/universe i386 Packages [132 kB]
Get:33 http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages [6,224 B]
Get:34 http://us.archive.ubuntu.com vivid-updates/main Translation-en [127 kB] 
Get:35 http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en [2,743 B]
Get:36 http://us.archive.ubuntu.com vivid-updates/restricted Translation-en [3,112 B]
Get:37 http://us.archive.ubuntu.com vivid-updates/universe Translation-en [78.2 kB]
Hit http://us.archive.ubuntu.com vivid-backports/restricted Sources            
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Sources            
Hit http://us.archive.ubuntu.com vivid-backports/restricted amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/multiverse amd64 Packages     
Hit http://us.archive.ubuntu.com vivid-backports/restricted i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/multiverse i386 Packages      
Hit http://us.archive.ubuntu.com vivid-backports/multiverse Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/restricted Translation-en     
Hit http://us.archive.ubuntu.com vivid-backports/main Sources                  
Hit http://us.archive.ubuntu.com vivid-backports/universe Sources              
Hit http://us.archive.ubuntu.com vivid-backports/main amd64 Packages           
Ign http://download.opensuse.org  Translation-en_US                            
Hit http://us.archive.ubuntu.com vivid-backports/universe amd64 Packages       
Hit http://us.archive.ubuntu.com vivid-backports/main i386 Packages            
Hit http://us.archive.ubuntu.com vivid-backports/universe i386 Packages        
Hit http://us.archive.ubuntu.com vivid-backports/main Translation-en           
Hit http://us.archive.ubuntu.com vivid-backports/universe Translation-en       
Ign http://download.opensuse.org  Translation-en                               
Fetched 2,136 kB in 59s (36.0 kB/s)                                            
Reading package lists... Done
W: Duplicate sources.list entry http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/  Packages (/var/lib/apt/lists/download.opensuse.org_repositories_home:_emby_xUbuntu%5f15.04_Packages)
W: You may want to run apt-get update to correct these problems
andre@NAS:~$ sudo apt-get install emby-server
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  libembymagickcore-6.q8-2 libembymagickwand-6.q8-2
The following NEW packages will be installed:
  emby-server libembymagickcore-6.q8-2 libembymagickwand-6.q8-2
0 upgraded, 3 newly installed, 0 to remove and 34 not upgraded.
Need to get 0 B/15.2 MB of archives.
After this operation, 55.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Preconfiguring packages ...
(Reading database ... 223721 files and directories currently installed.)
Preparing to unpack .../libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb ...
Unpacking libembymagickcore-6.q8-2:amd64 (8:6.9.2-8) ...
dpkg: error processing archive /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickCore-6.Q8.so.2.0.0', which is also in package libmagickcore-6.q8-2:amd64 8:6.9.1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Preparing to unpack .../libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb ...
Unpacking libembymagickwand-6.q8-2:amd64 (8:6.9.2-8) ...
dpkg: error processing archive /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8.so.2.0.0', which is also in package libmagickwand-6.q8-2:amd64 8:6.9.1-2
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Selecting previously unselected package emby-server.
Preparing to unpack .../emby-server_3.0.5781.5_all.deb ...
Unpacking emby-server (3.0.5781.5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (219-7ubuntu6) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb
 /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by Bashing-om on 2015-12-18
andre46; Welp;

Still with a version conflict .. and with the new attempt to install emby-serfver , a duplication in that source listing.

Let's take a look and see what we have to work with, and to work out of.

What is on the system that dpkg is attempting to install:
```

ls -al /var/cache/apt/archives/libembymagickcore-6.q8*
ls -al /var/cache/apt/archives/libembymagickwand-6.q8-2
ls -al /usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8*

```
We only consider at this time to remove the cache, maybe see what the system wants to bring back in . 
Presently, what is the system working with:
```

apt-cache policy libembymagickcore-6.q8
apt-cache policy libMagickWand-6.Q8

```

And in the attempt to install embey-server, did it install the package scripts by any  chance that will enable us to remove it ?
```

ls -al /var/lib/dpkg/info/emby-server.prerm
ls -al /var/lib/dpkg/info/emby-server.postrm

```

As a means of last resort, we might resort to "forcing" the removal of emby-server and deal the the consequences . But without the guidance of the install scrips, will sure be dicey .

[INDENT][INDENT]in spite of all our difficulties
[INDENT][INDENT][INDENT]there must be a graceful way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-21
Sorry for the late response again!  Busy time of year - not home much, but I'm around tonight and tomorrow night.  Here's what we got:

```
andre@NAS:~$ ls -al /var/cache/apt/archives/libembymagickcore-6.q8*
-rw-r--r-- 1 root root 1354486 Dec  8 18:12 /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb
andre@NAS:~$ ls -al /var/cache/apt/archives/libembymagickwand-6.q8-2
ls: cannot access /var/cache/apt/archives/libembymagickwand-6.q8-2: No such file or directory
andre@NAS:~$ ls -al /usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8*
lrwxrwxrwx 1 root root      27 Jun  2  2015 /usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8.so.2 -> libMagickWand-6.Q8.so.2.0.0
-rw-r--r-- 1 root root 1196720 Jun  2  2015 /usr/lib/x86_64-linux-gnu/libMagickWand-6.Q8.so.2.0.0
andre@NAS:~$ apt-cache policy libembymagickcore-6.q8
libembymagickcore-6.q8-2:
  Installed: (none)
  Candidate: 8:6.9.2-8
  Version table:
     8:6.9.2-8 0
        500 http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/  Packages
andre@NAS:~$ apt-cache policy libMagickWand-6.Q8
libmagickwand-6.q8-dev:
  Installed: (none)
  Candidate: 8:6.9.1-2
  Version table:
     8:6.9.1-2 0
        500 http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/  Packages
libmagickwand-6.q8-2:
  Installed: 8:6.9.1-2
  Candidate: 8:6.9.1-2
  Version table:
 *** 8:6.9.1-2 0
        500 http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/  Packages
        100 /var/lib/dpkg/status
andre@NAS:~$ ls -al /var/lib/dpkg/info/emby-server.prerm
-rwxr-xr-x 1 root root 2027 Dec  8 14:39 /var/lib/dpkg/info/emby-server.prerm
andre@NAS:~$ ls -al /var/lib/dpkg/info/emby-server.postrm
-rwxr-xr-x 1 root root 2124 Dec  8 14:39 /var/lib/dpkg/info/emby-server.postrm
```

---

### Post by Bashing-om on 2015-12-21
andre46; Well, Well well ....

That do look hopeful ... the config scripts did install for emby-server !

let's try:
```

sudo rm /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb
sudo apt-get --purge remove emby-server
sudo apt-get --purge remove openmediavault-emby

```

Anything left in the cache we need to look at ?
what returns:
```

ls -al /var/cache/apt/archives/libembymagick*

```

If that runs clean ... next is to find both the sources for emby-server and remove them.

Once these sources are removed so the package manager will not fetch emby-server anymore 
Then
we can get a new status from the update/upgrade process.

[INDENT][INDENT][INDENT]good things can happen
[/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-21
I don't think this fits your definition of "clean", but I'll wait for you to let me know :)
```
andre@NAS:~$ sudo rm /var/cache/apt/archives/libembymagickcore-6.q8-2_8%3a6.9.2-8_amd64.deb[sudo] password for andre: 
andre@NAS:~$ sudo apt-get --purge remove emby-server
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libart-2.0-2 libbonoboui2-0 libbonoboui2-common libgail18 libgdiplus
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libmono-2.0-dev libmono-accessibility4.0-cil libmono-c5-1.1-cil
  libmono-cairo4.0-cil libmono-cecil-private-cil libmono-cil-dev
  libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil
  libmono-cscompmgd0.0-cil libmono-csharp4.0c-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft4.0a-cil libmono-http4.0-cil libmono-ldap4.0-cil
  libmono-management4.0-cil libmono-messaging-rabbitmq4.0-cil
  libmono-messaging4.0-cil libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build4.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-oracle4.0-cil
  libmono-parallel4.0-cil libmono-peapi4.0a-cil libmono-posix4.0-cil
  libmono-rabbitmq4.0-cil libmono-relaxng4.0-cil libmono-sharpzip4.84-cil
  libmono-simd4.0-cil libmono-smdiagnostics0.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil
  libmono-system-data-entity4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil
  libmono-system-io-compression-filesystem4.0-cil
  libmono-system-io-compression4.0-cil libmono-system-json-microsoft4.0-cil
  libmono-system-json4.0-cil libmono-system-ldap-protocols4.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net-http-formatting4.0-cil
  libmono-system-net-http-webrequest4.0-cil libmono-system-net-http4.0-cil
  libmono-system-net4.0-cil libmono-system-numerics4.0-cil
  libmono-system-reactive-core2.2-cil libmono-system-reactive-debugger2.2-cil
  libmono-system-reactive-experimental2.2-cil
  libmono-system-reactive-interfaces2.2-cil
  libmono-system-reactive-linq2.2-cil
  libmono-system-reactive-observable-aliases0.0-cil
  libmono-system-reactive-platformservices2.2-cil
  libmono-system-reactive-providers2.2-cil
  libmono-system-reactive-runtime-remoting2.2-cil
  libmono-system-reactive-windows-forms2.2-cil
  libmono-system-reactive-windows-threading2.2-cil
  libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime4.0-cil
  libmono-system-servicemodel-activation4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-internals0.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil
  libmono-system-serviceprocess4.0-cil
  libmono-system-threading-tasks-dataflow4.0-cil
  libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-http-selfhost4.0-cil
  libmono-system-web-http-webhost4.0-cil libmono-system-web-http4.0-cil
  libmono-system-web-mvc3.0-cil libmono-system-web-razor2.0-cil
  libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
  libmono-system-web-webpages-deployment2.0-cil
  libmono-system-web-webpages-razor2.0-cil libmono-system-web-webpages2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0a-cil
  libmono-system-windows-forms4.0-cil libmono-system-windows4.0-cil
  libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml-serialization4.0-cil libmono-tasklets4.0-cil
  libmono-webbrowser4.0-cil libmono-webmatrix-data4.0-cil
  libmono-windowsbase4.0-cil libmono-xbuild-tasks4.0-cil libmonoboehm-2.0-1
  libmonoboehm-2.0-dev libnunit-cil-dev libnunit-console-runner2.6.3-cil
  libnunit-core-interfaces2.6.3-cil libnunit-core2.6.3-cil
  libnunit-framework2.6.3-cil libnunit-mocks2.6.3-cil libnunit-util2.6.3-cil
  mono-csharp-shell mono-devel mono-mcs mono-xbuild
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  emby-server*
0 upgraded, 0 newly installed, 1 to remove and 34 not upgraded.
1 not fully installed or removed.
After this operation, 48.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 224744 files and directories currently installed.)
Removing emby-server (3.0.5781.5) ...
Purging configuration files for emby-server (3.0.5781.5) ...
0
userdel: user 'emby' does not exist
debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable
dpkg: error processing package emby-server (--purge):
 subprocess installed post-removal script returned error exit status 1
E: Sub-process /usr/bin/dpkg returned an error code (1)
andre@NAS:~$ sudo apt-get --purge remove openmediavault-emby
Reading package lists... Done
Building dependency tree        
Reading state information... Done
E: Unable to locate package openmediavault-emby
andre@NAS:~$ ls -al /var/cache/apt/archives/libembymagick*
-rw-r--r-- 1 root root 247220 Dec  8 18:12 /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb
```

---

### Post by Bashing-om on 2015-12-21
andre46; Hummm ...

Hard to tell, maybe it did something.

What now ?
```

dpkg -l | grep emby

```

shucks too - thought that " libembymagickwand-6.q8-2" showed not to exist ..
remove it :
```

sudo apt-get clean /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb

```
as a 'cleaner' way to do it.

still pending is removing the source fetches .

[INDENT]3 steps forward and only 2 back?
[/INDENT]

---

### Post by andre46 on 2015-12-21
not much to send back to you this time around!
```
andre@NAS:~$ dpkg -l | grep embypc  emby-server                                                 3.0.5781.5                              all          Emby Server is a home media server.
andre@NAS:~$ sudo apt-get clean /var/cache/apt/archives/libembymagickwand-6.q8-2_8%3a6.9.2-8_amd64.deb
[sudo] password for andre: 
andre@NAS:~$ 
```

---

### Post by Bashing-om on 2015-12-21
andre46; Looks ->

Outstanding !

OK, now to find and remove the emby-server fetches.

Show:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

We remove them .. then we update/upgrade/-f/autoremove !

maybe all
[INDENT][INDENT]finer than a frog's hair 
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-21
before I proceed... looks good?
```
andre@NAS:~$ cat -n /etc/apt/sources.list     1	# deb cdrom:[Lubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main multiverse restricted universe
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     6	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    11	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ vivid universe
    17	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    19	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    27	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    29	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	deb http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    37	deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu vivid-security main restricted
    40	deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
    41	deb http://security.ubuntu.com/ubuntu vivid-security universe
    42	deb-src http://security.ubuntu.com/ubuntu vivid-security universe
    43	deb http://security.ubuntu.com/ubuntu vivid-security multiverse
    44	deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	# deb http://archive.canonical.com/ubuntu utopic partner
    51	# deb-src http://archive.canonical.com/ubuntu utopic partner
    52	
andre@NAS:~$ tail -v -n +1 /etc/apt/sources.list.d/*
==> /etc/apt/sources.list.d/emby-server.list <==
deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/ /
deb http://download.opensuse.org/repositories/home:/emby/xUbuntu_15.04/ /


==> /etc/apt/sources.list.d/modriscoll-ubuntu-nzbget-utopic.list <==
# deb http://ppa.launchpad.net/modriscoll/nzbget/ubuntu vivid main # disabled on upgrade to vivid
# deb-src http://ppa.launchpad.net/modriscoll/nzbget/ubuntu utopic main


==> /etc/apt/sources.list.d/modriscoll-ubuntu-nzbget-utopic.list.distUpgrade <==
deb http://ppa.launchpad.net/modriscoll/nzbget/ubuntu utopic main
# deb-src http://ppa.launchpad.net/modriscoll/nzbget/ubuntu utopic main


==> /etc/apt/sources.list.d/nodesource.list <==
# deb https://deb.nodesource.com/node_0.12 vivid main # disabled on upgrade to vivid
# deb-src https://deb.nodesource.com/node_0.12 vivid main # disabled on upgrade to vivid


==> /etc/apt/sources.list.d/nodesource.list.distUpgrade <==
deb https://deb.nodesource.com/node_0.12 utopic main
deb-src https://deb.nodesource.com/node_0.12 utopic main


==> /etc/apt/sources.list.d/sonarr.list <==
# deb http://apt.sonarr.tv/ master main # disabled on upgrade to vivid


==> /etc/apt/sources.list.d/sonarr.list.distUpgrade <==
deb http://apt.sonarr.tv/ master main
```

---

### Post by Bashing-om on 2015-12-21
andre46: proceeding

Merrily along our way ->
1) "36	deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse
     37	deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) vivid-backports main restricted universe multiverse"
I strongly recommend these repos be disabled . One does not want out-of-release packages and libs with out a very good reason !

2) " 50	# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner
      51	# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) utopic partner"
I do recommend that this repo be in service ( enabled) .. good things that are tested are available in the repo .
change "utopic" to "vivid" and remove the starting '#" comment character ) 

3) Unless you have a desire and an active interest in the source code of any/all packages .. I would and do recommend that all the "deb-src http:" fetches be disabled . For reference is my /etc/apt/sources.list, In this install I have no need to see the source code and have them commented out:
[http://paste.ubuntu.com/14134338/](http://paste.ubuntu.com/14134338/)
update and upgrades are much faster and it saves some on the bandwidth usage .

4) remove the emby-server fetch:
```

sudo rm /etc/apt/sources.list.d/emby-server.list

```

Once these are done, onward !
```

sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean
sudo apt update
sudo apt upgrade
sudo apt-get -f install
sudo dpkg -C

```
[INDENT][INDENT][INDENT]are we done now ?
[/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-21
I think we've done it!
```
andre@NAS:~$ sudo rm /etc/apt/sources.list.d/emby-server.listandre@NAS:~$ sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
andre@NAS:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libart-2.0-2 libbonoboui2-0 libbonoboui2-common libgail18 libgdiplus
  libgnomecanvas2-0 libgnomecanvas2-common libgnomeui-0 libgnomeui-common
  libmono-2.0-dev libmono-accessibility4.0-cil libmono-c5-1.1-cil
  libmono-cairo4.0-cil libmono-cecil-private-cil libmono-cil-dev
  libmono-codecontracts4.0-cil libmono-compilerservices-symbolwriter4.0-cil
  libmono-cscompmgd0.0-cil libmono-csharp4.0c-cil
  libmono-custommarshalers4.0-cil libmono-data-tds4.0-cil libmono-db2-1.0-cil
  libmono-debugger-soft4.0a-cil libmono-http4.0-cil libmono-ldap4.0-cil
  libmono-management4.0-cil libmono-messaging-rabbitmq4.0-cil
  libmono-messaging4.0-cil libmono-microsoft-build-engine4.0-cil
  libmono-microsoft-build-framework4.0-cil
  libmono-microsoft-build-tasks-v4.0-4.0-cil
  libmono-microsoft-build-utilities-v4.0-4.0-cil
  libmono-microsoft-build4.0-cil libmono-microsoft-csharp4.0-cil
  libmono-microsoft-visualc10.0-cil
  libmono-microsoft-web-infrastructure1.0-cil libmono-oracle4.0-cil
  libmono-parallel4.0-cil libmono-peapi4.0a-cil libmono-posix4.0-cil
  libmono-rabbitmq4.0-cil libmono-relaxng4.0-cil libmono-sharpzip4.84-cil
  libmono-simd4.0-cil libmono-smdiagnostics0.0-cil libmono-sqlite4.0-cil
  libmono-system-componentmodel-composition4.0-cil
  libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration-install4.0-cil libmono-system-core4.0-cil
  libmono-system-data-datasetextensions4.0-cil
  libmono-system-data-entity4.0-cil libmono-system-data-linq4.0-cil
  libmono-system-data-services-client4.0-cil
  libmono-system-data-services4.0-cil libmono-system-data4.0-cil
  libmono-system-design4.0-cil libmono-system-drawing-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-dynamic4.0-cil
  libmono-system-enterpriseservices4.0-cil
  libmono-system-identitymodel-selectors4.0-cil
  libmono-system-identitymodel4.0-cil
  libmono-system-io-compression-filesystem4.0-cil
  libmono-system-io-compression4.0-cil libmono-system-json-microsoft4.0-cil
  libmono-system-json4.0-cil libmono-system-ldap-protocols4.0-cil
  libmono-system-ldap4.0-cil libmono-system-management4.0-cil
  libmono-system-messaging4.0-cil libmono-system-net-http-formatting4.0-cil
  libmono-system-net-http-webrequest4.0-cil libmono-system-net-http4.0-cil
  libmono-system-net4.0-cil libmono-system-numerics4.0-cil
  libmono-system-reactive-core2.2-cil libmono-system-reactive-debugger2.2-cil
  libmono-system-reactive-experimental2.2-cil
  libmono-system-reactive-interfaces2.2-cil
  libmono-system-reactive-linq2.2-cil
  libmono-system-reactive-observable-aliases0.0-cil
  libmono-system-reactive-platformservices2.2-cil
  libmono-system-reactive-providers2.2-cil
  libmono-system-reactive-runtime-remoting2.2-cil
  libmono-system-reactive-windows-forms2.2-cil
  libmono-system-reactive-windows-threading2.2-cil
  libmono-system-runtime-caching4.0-cil
  libmono-system-runtime-durableinstancing4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-runtime4.0-cil
  libmono-system-servicemodel-activation4.0-cil
  libmono-system-servicemodel-discovery4.0-cil
  libmono-system-servicemodel-internals0.0-cil
  libmono-system-servicemodel-routing4.0-cil
  libmono-system-servicemodel-web4.0-cil libmono-system-servicemodel4.0a-cil
  libmono-system-serviceprocess4.0-cil
  libmono-system-threading-tasks-dataflow4.0-cil
  libmono-system-transactions4.0-cil libmono-system-web-abstractions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-dynamicdata4.0-cil
  libmono-system-web-extensions-design4.0-cil
  libmono-system-web-extensions4.0-cil libmono-system-web-http-selfhost4.0-cil
  libmono-system-web-http-webhost4.0-cil libmono-system-web-http4.0-cil
  libmono-system-web-mvc3.0-cil libmono-system-web-razor2.0-cil
  libmono-system-web-routing4.0-cil libmono-system-web-services4.0-cil
  libmono-system-web-webpages-deployment2.0-cil
  libmono-system-web-webpages-razor2.0-cil libmono-system-web-webpages2.0-cil
  libmono-system-web4.0-cil
  libmono-system-windows-forms-datavisualization4.0a-cil
  libmono-system-windows-forms4.0-cil libmono-system-windows4.0-cil
  libmono-system-xaml4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml-serialization4.0-cil libmono-tasklets4.0-cil
  libmono-webbrowser4.0-cil libmono-webmatrix-data4.0-cil
  libmono-windowsbase4.0-cil libmono-xbuild-tasks4.0-cil libmonoboehm-2.0-1
  libmonoboehm-2.0-dev libnunit-cil-dev libnunit-console-runner2.6.3-cil
  libnunit-core-interfaces2.6.3-cil libnunit-core2.6.3-cil
  libnunit-framework2.6.3-cil libnunit-mocks2.6.3-cil libnunit-util2.6.3-cil
  mono-csharp-shell mono-devel mono-mcs mono-xbuild
0 upgraded, 0 newly installed, 141 to remove and 34 not upgraded.
After this operation, 102 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 223721 files and directories currently installed.)
Removing mono-devel (4.2.1.102-0xamarin1) ...
Removing libgnomeui-0:amd64 (2.24.5-3) ...
Removing libbonoboui2-0:amd64 (2.24.5-0ubuntu4) ...
Removing libgnomecanvas2-0:amd64 (2.30.3-2) ...
Removing libart-2.0-2:amd64 (2.3.21-2) ...
Removing libbonoboui2-common (2.24.5-0ubuntu4) ...
Removing libgail18:amd64 (2.24.27-0ubuntu1) ...
Removing libmono-cil-dev (4.2.1.102-0xamarin1) ...
Removing libmono-system-data-services4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-servicemodel-web4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-drawing-design4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-serviceprocess4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-dynamicdata4.0-cil (4.2.1.102-0xamarin1) ...
Removing libgnomecanvas2-common (2.30.3-2) ...
Removing libgnomeui-common (2.24.5-3) ...
Removing libmono-2.0-dev (4.2.1.102-0xamarin1) ...
Removing libmono-c5-1.1-cil (4.2.1.102-0xamarin1) ...
Removing libmono-cairo4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-codecontracts4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-debugger-soft4.0a-cil (4.2.1.102-0xamarin1) ...
Removing libmono-cecil-private-cil (4.2.1.102-0xamarin1) ...
Removing libmono-compilerservices-symbolwriter4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-cscompmgd0.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-mvc3.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-webpages-razor2.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-webpages2.0-cil (4.2.1.102-0xamarin1) ...
Removing mono-mcs (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-csharp4.0-cil (4.2.1.102-0xamarin1) ...
Removing mono-csharp-shell (4.2.1.102-0xamarin1) ...
Removing libmono-csharp4.0c-cil (4.2.1.102-0xamarin1) ...
Removing libmono-custommarshalers4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-routing4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-runtime-caching4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-db2-1.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-http4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-management4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-messaging-rabbitmq4.0-cil (4.2.1.102-0xamarin1) ...
Removing mono-xbuild (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-build-tasks-v4.0-4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-build-engine4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-build4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-build-utilities-v4.0-4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-build-framework4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-visualc10.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-http-webhost4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-webpages-deployment2.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-microsoft-web-infrastructure1.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-oracle4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-parallel4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-peapi4.0a-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-json-microsoft4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-observable-aliases0.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-rabbitmq4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-relaxng4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-sharpzip4.84-cil (4.2.1.102-0xamarin1) ...
Removing libmono-simd4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-smdiagnostics0.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-componentmodel-composition4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-data-entity4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-http-selfhost4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-http4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-management4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-data-datasetextensions4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-extensions4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-data-linq4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-data-services-client4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-extensions-design4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-windows-forms-datavisualization4.0a-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-dynamic4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-io-compression-filesystem4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-io-compression4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-json4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-ldap-protocols4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-net-http-formatting4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-net-http-webrequest4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-net-http4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-net4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-platformservices2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-providers2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-debugger2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-experimental2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-runtime-remoting2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-linq2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-windows-forms2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-windows-threading2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-runtime-durableinstancing4.0-cil (4.2.1.102-0xamarin1) ...
Removing libnunit-cil-dev (2.6.3+dfsg-1) ...
Removing libnunit-console-runner2.6.3-cil (2.6.3+dfsg-1) ...
Removing libnunit-console-runner2.6.3-cil from Mono
Removing libnunit-util2.6.3-cil (2.6.3+dfsg-1) ...
Removing libnunit-util2.6.3-cil from Mono
Removing libmono-system-runtime4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-servicemodel-routing4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-servicemodel-discovery4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-threading-tasks-dataflow4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-abstractions4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-razor2.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-windows4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-windowsbase4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-xaml4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-xml-linq4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-xml-serialization4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-tasklets4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-webmatrix-data4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-xbuild-tasks4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmonoboehm-2.0-dev (4.2.1.102-0xamarin1) ...
Removing libmonoboehm-2.0-1 (4.2.1.102-0xamarin1) ...
Removing libnunit-core2.6.3-cil (2.6.3+dfsg-1) ...
Removing libnunit-core2.6.3-cil from Mono
Removing libnunit-core-interfaces2.6.3-cil (2.6.3+dfsg-1) ...
Removing libnunit-core-interfaces2.6.3-cil from Mono
Removing libnunit-mocks2.6.3-cil (2.6.3+dfsg-1) ...
Removing libnunit-mocks2.6.3-cil from Mono
Removing libnunit-framework2.6.3-cil (2.6.3+dfsg-1) ...
Removing libnunit-framework2.6.3-cil from Mono
Removing libmono-system-reactive-core2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-reactive-interfaces2.2-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-design4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-servicemodel-activation4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-servicemodel4.0a-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-sqlite4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-messaging4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-messaging4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-componentmodel-dataannotations4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-configuration-install4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-identitymodel-selectors4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-identitymodel4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-runtime-serialization4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-servicemodel-internals0.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-applicationservices4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-web-services4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-windows-forms4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-drawing4.0-cil (4.2.1.102-0xamarin1) ...
Removing libgdiplus (3.6-1) ...
Removing libmono-accessibility4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-data4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-data-tds4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-ldap4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-ldap4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-core4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-posix4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-enterpriseservices4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-numerics4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-runtime-serialization-formatters-soap4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-system-transactions4.0-cil (4.2.1.102-0xamarin1) ...
Removing libmono-webbrowser4.0-cil (4.2.1.102-0xamarin1) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
andre@NAS:~$ sudo apt-get clean
andre@NAS:~$ sudo apt update
Hit http://security.ubuntu.com vivid-security InRelease
Hit http://us.archive.ubuntu.com vivid InRelease                              
Hit http://us.archive.ubuntu.com vivid-updates InRelease                      
Get:1 http://archive.canonical.com vivid InRelease [10.3 kB]                  
Hit http://security.ubuntu.com vivid-security/main amd64 Packages
Hit http://security.ubuntu.com vivid-security/restricted amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/main amd64 Packages                     
Hit http://us.archive.ubuntu.com vivid/restricted amd64 Packages       
Hit http://security.ubuntu.com vivid-security/universe amd64 Packages
Hit http://us.archive.ubuntu.com vivid/universe amd64 Packages                 
Hit http://security.ubuntu.com vivid-security/multiverse amd64 Packages        
Hit http://us.archive.ubuntu.com vivid/multiverse amd64 Packages               
Hit http://security.ubuntu.com vivid-security/main i386 Packages               
Hit http://us.archive.ubuntu.com vivid/main i386 Packages      
Hit http://security.ubuntu.com vivid-security/restricted i386 Packages         
Hit http://us.archive.ubuntu.com vivid/restricted i386 Packages                
Hit http://security.ubuntu.com vivid-security/universe i386 Packages           
Get:2 http://archive.canonical.com vivid/partner Sources [3,036 B]             
Hit http://us.archive.ubuntu.com vivid/universe i386 Packages                  
Hit http://security.ubuntu.com vivid-security/multiverse i386 Packages
Hit http://us.archive.ubuntu.com vivid/multiverse i386 Packages                
Hit http://security.ubuntu.com vivid-security/main Translation-en              
Hit http://security.ubuntu.com vivid-security/multiverse Translation-en        
Hit http://us.archive.ubuntu.com vivid/main Translation-en                     
Hit http://security.ubuntu.com vivid-security/restricted Translation-en        
Hit http://us.archive.ubuntu.com vivid/multiverse Translation-en               
Get:3 http://archive.canonical.com vivid/partner amd64 Packages [2,986 B]      
Hit http://security.ubuntu.com vivid-security/universe Translation-en          
Hit http://us.archive.ubuntu.com vivid/restricted Translation-en               
Hit http://us.archive.ubuntu.com vivid/universe Translation-en                 
Hit http://us.archive.ubuntu.com vivid-updates/main amd64 Packages  
Get:4 http://archive.canonical.com vivid/partner i386 Packages [3,303 B]
Hit http://us.archive.ubuntu.com vivid-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com vivid-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com vivid-updates/multiverse amd64 Packages
Get:5 http://archive.canonical.com vivid/partner Translation-en [1,973 B]
Hit http://us.archive.ubuntu.com vivid-updates/main i386 Packages              
Hit http://us.archive.ubuntu.com vivid-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com vivid-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com vivid-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com vivid-updates/main Translation-en
Hit http://us.archive.ubuntu.com vivid-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com vivid-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com vivid-updates/universe Translation-en
Fetched 21.6 kB in 14s (1,471 B/s)                                             
Reading package lists... Done
Building dependency tree       
Reading state information... Done
34 packages can be upgraded. Run 'apt list --upgradable' to see them.
andre@NAS:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.19.0-42 linux-headers-3.19.0-42-generic
  linux-image-3.19.0-42-generic linux-image-extra-3.19.0-42-generic
  linux-signed-image-3.19.0-42-generic
The following packages will be upgraded:
  bind9-host cups-filters cups-filters-core-drivers dnsutils firefox
  firefox-locale-en git git-core git-man grub-common grub-efi-amd64
  grub-efi-amd64-bin grub-efi-amd64-signed grub2-common libbind9-90
  libcupsfilters1 libdns-export100 libdns100 libfontembed1 libirs-export91
  libisc-export95 libisc95 libisccc90 libisccfg-export90 libisccfg90
  liblightdm-gobject-1-0 liblwres90 lightdm linux-generic
  linux-headers-generic linux-image-generic linux-libc-dev
  linux-signed-generic linux-signed-image-generic
34 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 121 MB of archives.
After this operation, 293 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libisc-export95 amd64 1:9.9.5.dfsg-9ubuntu0.4 [121 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libdns-export100 amd64 1:9.9.5.dfsg-9ubuntu0.4 [436 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libisccfg-export90 amd64 1:9.9.5.dfsg-9ubuntu0.4 [20.3 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libirs-export91 amd64 1:9.9.5.dfsg-9ubuntu0.4 [17.9 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libcupsfilters1 amd64 1.0.67-0ubuntu2.6 [80.3 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libfontembed1 amd64 1.0.67-0ubuntu2.6 [47.3 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main lightdm amd64 1.14.4-0ubuntu1 [112 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-image-3.19.0-42-generic amd64 3.19.0-42.48 [16.8 MB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main dnsutils amd64 1:9.9.5.dfsg-9ubuntu0.4 [98.4 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main bind9-host amd64 1:9.9.5.dfsg-9ubuntu0.4 [46.9 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libisc95 amd64 1:9.9.5.dfsg-9ubuntu0.4 [149 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libdns100 amd64 1:9.9.5.dfsg-9ubuntu0.4 [662 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libisccc90 amd64 1:9.9.5.dfsg-9ubuntu0.4 [16.0 kB]
Get:14 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libisccfg90 amd64 1:9.9.5.dfsg-9ubuntu0.4 [36.6 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main liblwres90 amd64 1:9.9.5.dfsg-9ubuntu0.4 [33.7 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main libbind9-90 amd64 1:9.9.5.dfsg-9ubuntu0.4 [22.7 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main cups-filters-core-drivers amd64 1.0.67-0ubuntu2.6 [97.5 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main cups-filters amd64 1.0.67-0ubuntu2.6 [465 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main firefox amd64 43.0+build1-0ubuntu0.15.04.1 [45.1 MB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main firefox-locale-en amd64 43.0+build1-0ubuntu0.15.04.1 [694 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main git-man all 1:2.1.4-2.1ubuntu0.1 [701 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main git amd64 1:2.1.4-2.1ubuntu0.1 [2,817 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main git-core all 1:2.1.4-2.1ubuntu0.1 [1,542 B]
Get:24 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main grub-efi-amd64-signed amd64 1.46.4+2.02~beta2-22ubuntu1.4 [245 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main grub-efi-amd64 amd64 2.02~beta2-22ubuntu1.4 [73.0 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main grub-efi-amd64-bin amd64 2.02~beta2-22ubuntu1.4 [654 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main grub2-common amd64 2.02~beta2-22ubuntu1.4 [510 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main grub-common amd64 2.02~beta2-22ubuntu1.4 [1,701 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main liblightdm-gobject-1-0 amd64 1.14.4-0ubuntu1 [35.2 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-image-extra-3.19.0-42-generic amd64 3.19.0-42.48 [38.5 MB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-generic amd64 3.19.0.42.41 [1,848 B]
Get:32 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-image-generic amd64 3.19.0.42.41 [2,306 B]
Get:33 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-signed-image-3.19.0-42-generic amd64 3.19.0-42.48 [4,032 B]
Get:34 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-signed-generic amd64 3.19.0.42.41 [1,882 B]
Get:35 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-signed-image-generic amd64 3.19.0.42.41 [2,340 B]
Get:36 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-headers-3.19.0-42 all 3.19.0-42.48 [9,353 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-headers-3.19.0-42-generic amd64 3.19.0-42.48 [752 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-headers-generic amd64 3.19.0.42.41 [2,272 B]
Get:39 http://us.archive.ubuntu.com/ubuntu/ vivid-updates/main linux-libc-dev amd64 3.19.0-42.48 [797 kB]
Fetched 121 MB in 1min 8s (1,779 kB/s)                                         
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 222168 files and directories currently installed.)
Preparing to unpack .../libisc-export95_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libisc-export95 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libdns-export100_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libdns-export100 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libisccfg-export90_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libisccfg-export90 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libirs-export91_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libirs-export91 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libcupsfilters1_1.0.67-0ubuntu2.6_amd64.deb ...
Unpacking libcupsfilters1:amd64 (1.0.67-0ubuntu2.6) over (1.0.67-0ubuntu2.5) ...
Preparing to unpack .../libfontembed1_1.0.67-0ubuntu2.6_amd64.deb ...
Unpacking libfontembed1:amd64 (1.0.67-0ubuntu2.6) over (1.0.67-0ubuntu2.5) ...
Preparing to unpack .../lightdm_1.14.4-0ubuntu1_amd64.deb ...
Unpacking lightdm (1.14.4-0ubuntu1) over (1.14.2-0ubuntu1.1) ...
Selecting previously unselected package linux-image-3.19.0-42-generic.
Preparing to unpack .../linux-image-3.19.0-42-generic_3.19.0-42.48_amd64.deb ...
Done.
Unpacking linux-image-3.19.0-42-generic (3.19.0-42.48) ...
Preparing to unpack .../dnsutils_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking dnsutils (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../bind9-host_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking bind9-host (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libisc95_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libisc95 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libdns100_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libdns100 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libisccc90_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libisccc90 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libisccfg90_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libisccfg90 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../liblwres90_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking liblwres90 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../libbind9-90_1%3a9.9.5.dfsg-9ubuntu0.4_amd64.deb ...
Unpacking libbind9-90 (1:9.9.5.dfsg-9ubuntu0.4) over (1:9.9.5.dfsg-9ubuntu0.3) ...
Preparing to unpack .../cups-filters-core-drivers_1.0.67-0ubuntu2.6_amd64.deb ...
Unpacking cups-filters-core-drivers (1.0.67-0ubuntu2.6) over (1.0.67-0ubuntu2.5) ...
Preparing to unpack .../cups-filters_1.0.67-0ubuntu2.6_amd64.deb ...
Unpacking cups-filters (1.0.67-0ubuntu2.6) over (1.0.67-0ubuntu2.5) ...
Preparing to unpack .../firefox_43.0+build1-0ubuntu0.15.04.1_amd64.deb ...
Unpacking firefox (43.0+build1-0ubuntu0.15.04.1) over (42.0+build2-0ubuntu0.15.04.1) ...
Preparing to unpack .../firefox-locale-en_43.0+build1-0ubuntu0.15.04.1_amd64.deb ...
Unpacking firefox-locale-en (43.0+build1-0ubuntu0.15.04.1) over (42.0+build2-0ubuntu0.15.04.1) ...
Preparing to unpack .../git-man_1%3a2.1.4-2.1ubuntu0.1_all.deb ...
Unpacking git-man (1:2.1.4-2.1ubuntu0.1) over (1:2.1.4-2.1) ...
Preparing to unpack .../git_1%3a2.1.4-2.1ubuntu0.1_amd64.deb ...
Unpacking git (1:2.1.4-2.1ubuntu0.1) over (1:2.1.4-2.1) ...
Preparing to unpack .../git-core_1%3a2.1.4-2.1ubuntu0.1_all.deb ...
Unpacking git-core (1:2.1.4-2.1ubuntu0.1) over (1:2.1.4-2.1) ...
Preparing to unpack .../grub-efi-amd64-signed_1.46.4+2.02~beta2-22ubuntu1.4_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.46.4+2.02~beta2-22ubuntu1.4) over (1.46.2+2.02~beta2-22ubuntu1.2) ...
Preparing to unpack .../grub-efi-amd64_2.02~beta2-22ubuntu1.4_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-22ubuntu1.4) over (2.02~beta2-22ubuntu1.2) ...
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-22ubuntu1.4_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-22ubuntu1.4) over (2.02~beta2-22ubuntu1.2) ...
Preparing to unpack .../grub2-common_2.02~beta2-22ubuntu1.4_amd64.deb ...
Unpacking grub2-common (2.02~beta2-22ubuntu1.4) over (2.02~beta2-22ubuntu1.2) ...
Preparing to unpack .../grub-common_2.02~beta2-22ubuntu1.4_amd64.deb ...
Unpacking grub-common (2.02~beta2-22ubuntu1.4) over (2.02~beta2-22ubuntu1.2) ...
Preparing to unpack .../liblightdm-gobject-1-0_1.14.4-0ubuntu1_amd64.deb ...
Unpacking liblightdm-gobject-1-0 (1.14.4-0ubuntu1) over (1.14.2-0ubuntu1.1) ...
Selecting previously unselected package linux-image-extra-3.19.0-42-generic.
Preparing to unpack .../linux-image-extra-3.19.0-42-generic_3.19.0-42.48_amd64.deb ...
Unpacking linux-image-extra-3.19.0-42-generic (3.19.0-42.48) ...
Preparing to unpack .../linux-generic_3.19.0.42.41_amd64.deb ...
Unpacking linux-generic (3.19.0.42.41) over (3.19.0.39.38) ...
Preparing to unpack .../linux-image-generic_3.19.0.42.41_amd64.deb ...
Unpacking linux-image-generic (3.19.0.42.41) over (3.19.0.39.38) ...
Selecting previously unselected package linux-signed-image-3.19.0-42-generic.
Preparing to unpack .../linux-signed-image-3.19.0-42-generic_3.19.0-42.48_amd64.deb ...
Unpacking linux-signed-image-3.19.0-42-generic (3.19.0-42.48) ...
Preparing to unpack .../linux-signed-generic_3.19.0.42.41_amd64.deb ...
Unpacking linux-signed-generic (3.19.0.42.41) over (3.19.0.39.38) ...
Preparing to unpack .../linux-signed-image-generic_3.19.0.42.41_amd64.deb ...
Unpacking linux-signed-image-generic (3.19.0.42.41) over (3.19.0.39.38) ...
Selecting previously unselected package linux-headers-3.19.0-42.
Preparing to unpack .../linux-headers-3.19.0-42_3.19.0-42.48_all.deb ...
Unpacking linux-headers-3.19.0-42 (3.19.0-42.48) ...
Selecting previously unselected package linux-headers-3.19.0-42-generic.
Preparing to unpack .../linux-headers-3.19.0-42-generic_3.19.0-42.48_amd64.deb ...
Unpacking linux-headers-3.19.0-42-generic (3.19.0-42.48) ...
Preparing to unpack .../linux-headers-generic_3.19.0.42.41_amd64.deb ...
Unpacking linux-headers-generic (3.19.0.42.41) over (3.19.0.39.38) ...
Preparing to unpack .../linux-libc-dev_3.19.0-42.48_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.19.0-42.48) over (3.19.0-39.44) ...
Processing triggers for man-db (2.7.0.2-5) ...
Processing triggers for dbus (1.8.12-1ubuntu5) ...
Processing triggers for ureadahead (0.100.0-19) ...
Processing triggers for systemd (219-7ubuntu6) ...
Processing triggers for cups (2.0.2-1ubuntu3.2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu3) ...
Processing triggers for mime-support (3.58ubuntu1) ...
Processing triggers for install-info (5.2.0.dfsg.1-6) ...
Setting up libisc-export95 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libdns-export100 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libisccfg-export90 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libirs-export91 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libcupsfilters1:amd64 (1.0.67-0ubuntu2.6) ...
Setting up libfontembed1:amd64 (1.0.67-0ubuntu2.6) ...
Setting up lightdm (1.14.4-0ubuntu1) ...
Installing new version of config file /etc/apparmor.d/abstractions/lightdm_chromium-browser ...
Installing new version of config file /etc/pam.d/lightdm ...
Installing new version of config file /etc/pam.d/lightdm-autologin ...
Setting up linux-image-3.19.0-42-generic (3.19.0-42.48) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up libisc95 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libdns100 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libisccc90 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libisccfg90 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up libbind9-90 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up liblwres90 (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up bind9-host (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up dnsutils (1:9.9.5.dfsg-9ubuntu0.4) ...
Setting up cups-filters-core-drivers (1.0.67-0ubuntu2.6) ...
Setting up cups-filters (1.0.67-0ubuntu2.6) ...


Setting up firefox (43.0+build1-0ubuntu0.15.04.1) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (43.0+build1-0ubuntu0.15.04.1) ...
Setting up git-man (1:2.1.4-2.1ubuntu0.1) ...
Setting up git (1:2.1.4-2.1ubuntu0.1) ...
Setting up git-core (1:2.1.4-2.1ubuntu0.1) ...
Setting up grub-common (2.02~beta2-22ubuntu1.4) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-22ubuntu1.4) ...
Setting up grub-efi-amd64-bin (2.02~beta2-22ubuntu1.4) ...
Setting up grub-efi-amd64 (2.02~beta2-22ubuntu1.4) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up grub-efi-amd64-signed (1.46.4+2.02~beta2-22ubuntu1.4) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up liblightdm-gobject-1-0 (1.14.4-0ubuntu1) ...
Setting up linux-image-extra-3.19.0-42-generic (3.19.0-42.48) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (3.19.0.42.41) ...
Setting up linux-headers-3.19.0-42 (3.19.0-42.48) ...
Setting up linux-headers-3.19.0-42-generic (3.19.0-42.48) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.19.0-42-generic /boot/vmlinuz-3.19.0-42-generic
Setting up linux-headers-generic (3.19.0.42.41) ...
Setting up linux-generic (3.19.0.42.41) ...
Setting up linux-signed-image-3.19.0-42-generic (3.19.0-42.48) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-generic (3.19.0.42.41) ...
Setting up linux-signed-generic (3.19.0.42.41) ...
Setting up linux-libc-dev:amd64 (3.19.0-42.48) ...
Processing triggers for libc-bin (2.21-0ubuntu4) ...
andre@NAS:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
andre@NAS:~$ sudo dpkg -C
andre@NAS:~$ cat -n /etc/apt/sources.list
     1	# deb cdrom:[Lubuntu 14.10 _Utopic Unicorn_ - Release amd64 (20141022.1)]/ utopic main multiverse restricted universe
     2	
     3	# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     4	# newer versions of the distribution.
     5	deb http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     6	#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ vivid main restricted
     7	
     8	## Major bug fix updates produced after the final release of the
     9	## distribution.
    10	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    11	#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates main restricted
    12	
    13	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14	## team. Also, please note that software in universe WILL NOT receive any
    15	## review or updates from the Ubuntu security team.
    16	deb http://us.archive.ubuntu.com/ubuntu/ vivid universe
    17	#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ vivid universe
    18	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    19	#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates universe
    20	
    21	## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    22	## team, and may not be under a free licence. Please satisfy yourself as to 
    23	## your rights to use the software. Also, please note that software in 
    24	## multiverse WILL NOT receive any review or updates from the Ubuntu
    25	## security team.
    26	deb http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    27	#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ vivid multiverse
    28	deb http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    29	#(bdq)deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-updates multiverse
    30	
    31	## N.B. software from this repository may not have been tested as
    32	## extensively as that contained in the main release, although it includes
    33	## newer versions of some applications which may provide useful features.
    34	## Also, please note that software in backports WILL NOT receive any review
    35	## or updates from the Ubuntu security team.
    36	#deb http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    37	#deb-src http://us.archive.ubuntu.com/ubuntu/ vivid-backports main restricted universe multiverse
    38	
    39	deb http://security.ubuntu.com/ubuntu vivid-security main restricted
    40	#(bdq)deb-src http://security.ubuntu.com/ubuntu vivid-security main restricted
    41	deb http://security.ubuntu.com/ubuntu vivid-security universe
    42	#(bdq)deb-src http://security.ubuntu.com/ubuntu vivid-security universe
    43	deb http://security.ubuntu.com/ubuntu vivid-security multiverse
    44	#(bdq)deb-src http://security.ubuntu.com/ubuntu vivid-security multiverse
    45	
    46	## Uncomment the following two lines to add software from Canonical's
    47	## 'partner' repository.
    48	## This software is not part of Ubuntu, but is offered by Canonical and the
    49	## respective vendors as a service to Ubuntu users.
    50	deb http://archive.canonical.com/ubuntu vivid partner
    51	deb-src http://archive.canonical.com/ubuntu vivid partner
    52
```

---

### Post by Bashing-om on 2015-12-21
andre46; By Golly !

Who said it could not be done ! I think we dood it !

For a final systems check:
```

df -h
df -i
dpkg -l | grep linux-

```

I bet we can wipe the sweat off
[INDENT][INDENT][INDENT]now
[/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-22
How we looking?
```
andre@NAS:~$ df -hFilesystem      Size  Used Avail Use% Mounted on
udev            788M     0  788M   0% /dev
tmpfs           160M   14M  146M   9% /run
/dev/sda2       292G   15G  263G   6% /
tmpfs           799M  4.0K  799M   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           799M     0  799M   0% /sys/fs/cgroup
/dev/sda1       511M  3.4M  508M   1% /boot/efi
tmpfs           160M   36K  160M   1% /run/user/1000
/dev/sdh1       1.8T  1.4T  329G  82% /media/andre/2TB
/dev/sdg1       4.6T  3.2T  1.2T  73% /media/andre/5TB_2
/dev/sdf1       3.6T  2.0T  1.5T  57% /media/andre/4TB_1
/dev/sde1       4.6T  3.6T  787G  83% /media/andre/5TB_1
/dev/sdd1       1.9T  1.9G  1.9T   1% /media/andre/Transfer Drive
/dev/sdc1       3.6T  1.5T  2.0T  43% /media/andre/4TB_3
/dev/sdb1       3.6T  2.9T  602G  83% /media/andre/4TB_2
andre@NAS:~$ df -i
Filesystem         Inodes  IUsed      IFree IUse% Mounted on
udev               201674    634     201040    1% /dev
tmpfs              204455    913     203542    1% /run
/dev/sda2        19398656 320135   19078521    2% /
tmpfs              204455      3     204452    1% /dev/shm
tmpfs              204455      8     204447    1% /run/lock
tmpfs              204455     15     204440    1% /sys/fs/cgroup
/dev/sda1               0      0          0     - /boot/efi
tmpfs              204455     21     204434    1% /run/user/1000
/dev/sdh1       122101760  87692  122014068    1% /media/andre/2TB
/dev/sdg1       152621056  24474  152596582    1% /media/andre/5TB_2
/dev/sdf1       244146176   9910  244136266    1% /media/andre/4TB_1
/dev/sde1       152621056  24009  152597047    1% /media/andre/5TB_1
/dev/sdd1      1951702460    331 1951702129    1% /media/andre/Transfer Drive
/dev/sdc1       244195328   2945  244192383    1% /media/andre/4TB_3
/dev/sdb1       244195328  20753  244174575    1% /media/andre/4TB_2
andre@NAS:~$ dpkg -l | grep linux-
ii  linux-firmware                        1.143.7                                 all          Firmware for Linux kernel drivers
ii  linux-generic                         3.19.0.42.41                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-28               3.19.0-28.30                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic       3.19.0-28.30                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30               3.19.0-30.34                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic       3.19.0-30.34                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-37               3.19.0-37.42                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-37-generic       3.19.0-37.42                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-39               3.19.0-39.44                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-39-generic       3.19.0-39.44                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-42               3.19.0-42.48                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic       3.19.0-42.48                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                 3.19.0.42.41                            amd64        Generic Linux kernel headers
rc  linux-image-3.19.0-26-generic         3.19.0-26.28                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-28-generic         3.19.0-28.30                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic         3.19.0-30.34                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic         3.19.0-37.42                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic         3.19.0-39.44                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic         3.19.0-42.48                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-26-generic   3.19.0-26.28                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic   3.19.0-28.30                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic   3.19.0-30.34                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-37-generic   3.19.0-37.42                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-39-generic   3.19.0-39.44                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic   3.19.0-42.48                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.19.0.42.41                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  3.19.0-42.48                            amd64        Linux Kernel Headers for development
ii  linux-signed-generic                  3.19.0.42.41                            amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.19.0-26-generic  3.19.0-26.28                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-28-generic  3.19.0-28.30                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-30-generic  3.19.0-30.34                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-37-generic  3.19.0-37.42                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-39-generic  3.19.0-39.44                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-42-generic  3.19.0-42.48                            amd64        Signed kernel image generic
ii  linux-signed-image-generic            3.19.0.42.41                            amd64        Signed Generic Linux kernel image
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                       3:6.03+dfsg-5ubuntu1                    all          collection of bootloaders (common)
ii  syslinux-legacy                       2:3.63+dfsg-2ubuntu6                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by Bashing-om on 2015-12-22
andre46; Well ..

Looks good, but, I do not know the why that "autoremove" did not remove the old kernels .
Recon we can do that ourselfs.
What kernel are you now booting ?
```

uname -r

```
And we clean up those old no longer needed kernels .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-22
I'm using 3.19.0-39-generic

---

### Post by Bashing-om on 2015-12-22
andre46; Ho Kay ..

Let's run:
```

sudo apt-get purge linux-image{,extra}-3.19.0-{28,30,37}-generic
sudo apt-get purge linux-headers-3.19.0-{28,30,37} {,generic}
sudo apt-get purge linux-signed-image-3.19.0-{28,30,37}-generic
dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge

```

Now what do you look like :
```

dpkg -l | grep linux-

```

[INDENT][INDENT]all better now
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-22
I'm not certain this all went down as you expected, but here's what we got:
```
andre@NAS:~$ sudo apt-get purge linux-image-{,extra}-3.19.0-{28,30,37}-generic[sudo] password for andre: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image--3.19.0-28-generic
E: Couldn't find any package by regex 'linux-image--3.19.0-28-generic'
E: Unable to locate package linux-image--3.19.0-30-generic
E: Couldn't find any package by regex 'linux-image--3.19.0-30-generic'
E: Unable to locate package linux-image--3.19.0-37-generic
E: Couldn't find any package by regex 'linux-image--3.19.0-37-generic'
andre@NAS:~$ sudo apt-get purge linux-headers-3.19.0-{28,30,37} {,generic}
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package generic
andre@NAS:~$ sudo apt-get purge linux-signed-image-3.19.0-{28,30,37}-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-signed-image-3.19.0-28-generic* linux-signed-image-3.19.0-30-generic*
  linux-signed-image-3.19.0-37-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 117 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 252360 files and directories currently installed.)
Removing linux-signed-image-3.19.0-28-generic (3.19.0-28.30) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.19.0-28-generic (3.19.0-28.30) ...
Removing linux-signed-image-3.19.0-30-generic (3.19.0-30.34) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.19.0-30-generic (3.19.0-30.34) ...
Removing linux-signed-image-3.19.0-37-generic (3.19.0-37.42) ...
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-30-generic
Found initrd image: /boot/initrd.img-3.19.0-30-generic
Found linux image: /boot/vmlinuz-3.19.0-28-generic
Found initrd image: /boot/initrd.img-3.19.0-28-generic
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-signed-image-3.19.0-37-generic (3.19.0-37.42) ...
andre@NAS:~$ dpkg --list |grep "^rc" | cut -d " " -f 3 | xargs sudo dpkg --purge(Reading database ... 252348 files and directories currently installed.)
Removing ca-certificates-mono (4.2.1.102-0xamarin1) ...
Purging configuration files for ca-certificates-mono (4.2.1.102-0xamarin1) ...
Removing libart-2.0-2:amd64 (2.3.21-2) ...
Purging configuration files for libart-2.0-2:amd64 (2.3.21-2) ...
Removing libbonoboui2-0:amd64 (2.24.5-0ubuntu4) ...
Purging configuration files for libbonoboui2-0:amd64 (2.24.5-0ubuntu4) ...
Removing libgail18:amd64 (2.24.27-0ubuntu1) ...
Purging configuration files for libgail18:amd64 (2.24.27-0ubuntu1) ...
Removing libgdiplus (3.6-1) ...
Purging configuration files for libgdiplus (3.6-1) ...
Removing libgnomecanvas2-0:amd64 (2.30.3-2) ...
Purging configuration files for libgnomecanvas2-0:amd64 (2.30.3-2) ...
Removing libgnomeui-0:amd64 (2.24.5-3) ...
Purging configuration files for libgnomeui-0:amd64 (2.24.5-3) ...
Removing libmonoboehm-2.0-1 (4.2.1.102-0xamarin1) ...
Purging configuration files for libmonoboehm-2.0-1 (4.2.1.102-0xamarin1) ...
Removing linux-image-3.19.0-26-generic (3.19.0-26.28) ...
Purging configuration files for linux-image-3.19.0-26-generic (3.19.0-26.28) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-26-generic /boot/vmlinuz-3.19.0-26-generic
Removing linux-image-extra-3.19.0-26-generic (3.19.0-26.28) ...
Purging configuration files for linux-image-extra-3.19.0-26-generic (3.19.0-26.28) ...
Removing linux-signed-image-3.19.0-26-generic (3.19.0-26.28) ...
Purging configuration files for linux-signed-image-3.19.0-26-generic (3.19.0-26.28) ...
Removing mono-devel (4.2.1.102-0xamarin1) ...
Purging configuration files for mono-devel (4.2.1.102-0xamarin1) ...
andre@NAS:~$ dpkg -l | grep linux-
ii  linux-firmware                        1.143.7                                 all          Firmware for Linux kernel drivers
ii  linux-generic                         3.19.0.42.41                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-28               3.19.0-28.30                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic       3.19.0-28.30                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30               3.19.0-30.34                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic       3.19.0-30.34                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-37               3.19.0-37.42                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-37-generic       3.19.0-37.42                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-39               3.19.0-39.44                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-39-generic       3.19.0-39.44                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-42               3.19.0-42.48                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic       3.19.0-42.48                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                 3.19.0.42.41                            amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-28-generic         3.19.0-28.30                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic         3.19.0-30.34                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic         3.19.0-37.42                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic         3.19.0-39.44                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic         3.19.0-42.48                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic   3.19.0-28.30                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic   3.19.0-30.34                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-37-generic   3.19.0-37.42                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-39-generic   3.19.0-39.44                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic   3.19.0-42.48                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.19.0.42.41                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  3.19.0-42.48                            amd64        Linux Kernel Headers for development
ii  linux-signed-generic                  3.19.0.42.41                            amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.19.0-39-generic  3.19.0-39.44                            amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-42-generic  3.19.0-42.48                            amd64        Signed kernel image generic
ii  linux-signed-image-generic            3.19.0.42.41                            amd64        Signed Generic Linux kernel image
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                       3:6.03+dfsg-5ubuntu1                    all          collection of bootloaders (common)
ii  syslinux-legacy                       2:3.63+dfsg-2ubuntu6                    amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by Bashing-om on 2015-12-22
andre46' Oooopps ...

My bad - nother typo ( one other was brought to my attention)
Too late now to  re-run it correctly .
it should have been " sudo apt-get purge linux-image{,extra}-3.19.0-{28,30,37}-generic"
I had an additional '-' after " {,extra} .

Show now what we have to work with :
```

dpkg -l | grep linux-

```

let's see what it is going to take to make things right.

[INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2015-12-23
andre46; Morning ...

Back to it ..

Assuming there is no change from:
> 
andre@NAS:~$ dpkg -l | grep linux-
ii  linux-firmware                        1.143.7                                 all          Firmware for Linux kernel drivers
ii  linux-generic                         3.19.0.42.41                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.19.0-28               3.19.0-28.30                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-28-generic       3.19.0-28.30                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-30               3.19.0-30.34                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-30-generic       3.19.0-30.34                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-37               3.19.0-37.42                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-37-generic       3.19.0-37.42                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-39               3.19.0-39.44                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-39-generic       3.19.0-39.44                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-42               3.19.0-42.48                            all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic       3.19.0-42.48                            amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                 3.19.0.42.41                            amd64        Generic Linux kernel headers
ii  linux-image-3.19.0-28-generic         3.19.0-28.30                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-30-generic         3.19.0-30.34                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-37-generic         3.19.0-37.42                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-39-generic         3.19.0-39.44                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-42-generic         3.19.0-42.48                            amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-28-generic   3.19.0-28.30                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-30-generic   3.19.0-30.34                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-37-generic   3.19.0-37.42                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-39-generic   3.19.0-39.44                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic   3.19.0-42.48                            amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                   3.19.0.42.41                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  3.19.0-42.48                            amd64        Linux Kernel Headers for development
ii 


Let's straighten this up in smaller stages:
```

sudo apt-get purge linux-image-3.19.0-{28,30,37}-generic
sudo apt-get purge linux-headers-3.19.0-{28,30,37-generic 
sudo apt-get purge linux-headers-3.19.0-{28,30,37}
sudo apt-get purge linux-image-extra-3.19.0-{28,30,37}-generic

```

Ok, when that runs clean .. :
```

sudo update-grub

``` just for cheap insurance and we can the more easily look for any errors the system reports ...

All look'n good (?)... let's make sure there is no further clean up, and the system is in a consistent state:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
ls -al /vmlinuz*
ls -al /initrd.img*

```
That all the directory contents agree and that the booting kernel symlinks are now established correctly .

[INDENT][INDENT]behold that light
[INDENT][INDENT][INDENT]at the end of the this tunnel
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-27
Hey - sorry for the delay - holidays and all.  I'll be back home to try that tomorrow evening.  Thanks so much for your help thus far!

---

### Post by Bashing-om on 2015-12-28
andre46; Hey ...

No big hurry, I think we just about have this sloppyation whooped. Just a bit of clean up and call this done.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by andre46 on 2015-12-28
hope this looks good!
```
andre@NAS:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Adding boot menu entry for EFI firmware configuration
done
andre@NAS:~$ ls -al /usr/src/
total 28
drwxr-xr-x  7 root root 4096 Dec 28 18:03 .
drwxr-xr-x 11 root root 4096 Mar 27  2015 ..
drwxr-xr-x  4 root root 4096 Aug 31 21:23 fglrx-updates-core-15.200
drwxr-xr-x 24 root root 4096 Dec 14 18:17 linux-headers-3.19.0-39
drwxr-xr-x  7 root root 4096 Dec 14 18:17 linux-headers-3.19.0-39-generic
drwxr-xr-x 24 root root 4096 Dec 21 21:35 linux-headers-3.19.0-42
drwxr-xr-x  7 root root 4096 Dec 21 21:35 linux-headers-3.19.0-42-generic
andre@NAS:~$ ls -al /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 Dec 28 18:03 .
drwxr-xr-x 24 root root 4096 Aug 31 21:36 ..
drwxr-xr-x  6 root root 4096 Dec 14 18:18 3.19.0-39-generic
drwxr-xr-x  6 root root 4096 Dec 21 21:38 3.19.0-42-generic
andre@NAS:~$ ls -al /boot/
total 76984
drwxr-xr-x  4 root root     4096 Dec 28 17:59 .
drwxr-xr-x 23 root root     4096 Dec 28 18:08 ..
-rw-r--r--  1 root root  1271691 Dec  1 11:52 abi-3.19.0-39-generic
-rw-r--r--  1 root root  1271765 Dec 17 19:20 abi-3.19.0-42-generic
-rw-r--r--  1 root root   177782 Dec  1 11:52 config-3.19.0-39-generic
-rw-r--r--  1 root root   177800 Dec 17 19:20 config-3.19.0-42-generic
drwxr-xr-x  3 root root     4096 Dec 31  1969 efi
drwxr-xr-x  5 root root     4096 Dec 28 18:07 grub
-rw-r--r--  1 root root 20817324 Dec 14 18:15 initrd.img-3.19.0-39-generic
-rw-r--r--  1 root root 20819891 Dec 21 21:39 initrd.img-3.19.0-42-generic
-rw-r--r--  1 root root   164216 Mar  6  2015 memtest86+.bin
-rw-r--r--  1 root root   165892 Mar  6  2015 memtest86+.elf
-rw-r--r--  1 root root   166396 Mar  6  2015 memtest86+_multiboot.bin
-rw-------  1 root root  3622804 Dec  1 11:52 System.map-3.19.0-39-generic
-rw-------  1 root root  3622861 Dec 17 19:20 System.map-3.19.0-42-generic
-rw-------  1 root root  6624704 Dec  1 11:52 vmlinuz-3.19.0-39-generic
-rw-------  1 root root  6626616 Dec 14 18:16 vmlinuz-3.19.0-39-generic.efi.signed
-rw-------  1 root root  6625664 Dec 17 19:20 vmlinuz-3.19.0-42-generic
-rw-------  1 root root  6627576 Dec 21 21:39 vmlinuz-3.19.0-42-generic.efi.signed
andre@NAS:~$ ls -al /vmlinuz*
lrwxrwxrwx 1 root root 30 Dec 21 21:36 /vmlinuz -> boot/vmlinuz-3.19.0-42-generic
lrwxrwxrwx 1 root root 30 Dec 10 19:54 /vmlinuz.old -> boot/vmlinuz-3.19.0-39-generic
andre@NAS:~$ ls -al /initrd.img*
lrwxrwxrwx 1 root root 33 Dec 21 21:36 /initrd.img -> boot/initrd.img-3.19.0-42-generic
lrwxrwxrwx 1 root root 33 Dec 10 19:54 /initrd.img.old -> boot/initrd.img-3.19.0-39-generic
```

---

### Post by Bashing-om on 2015-12-28
andre46; Well ! 
Now

That looks absolutely perfect to me.

Can you think up any reason now that you can not mark this thread 'solved' ?
As I do think our mission here is completed .
If and only IF you agree:

Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]dirty deeds 
[INDENT][INDENT][INDENT]done dirt cheap
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

