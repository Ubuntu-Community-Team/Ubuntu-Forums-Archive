---
title: "Can't boot :("
date: 2012-11-27
forum: General Help
---

### Post by kindlykokokat on 2012-11-27
Hello.

I have a windows Vista machine with wubi of 11.04 which was updated to 11.10. Today I could not boot into the Ubuntu, after I was prompted by the windows bootloader to choose an OS and having chosen Ubuntu, normally it would take 1-2 seconds before the grub screen shows up, instead the screen turns the ubuntu-reddish-something-is-happening, then after about 10 seconds the CD drive spins up (I can hear) then down and the HDD light turns off and the computer stays in that state for 2 minutes, after which I restarted by holding the power button.

Just yesterday I updated with whatever the update manager showed me (I didn't take a look at the entries) and this is the first boot attempt since then.

I am on a core2E6300 with asus mobo and 7600gt graphics, I can boot into windows vista fine.

Thanks futurely for your help.

---

### Post by bcbc on 2012-11-28
What's the priority? Data recovery or getting the install booting?

Do you have an Ubuntu CD you can boot as a live CD?

---

### Post by kindlykokokat on 2012-11-28
I would like to be able to boot in so I can go back to work.

I do have a live CD

---

### Post by bcbc on 2012-11-28
Okay, boot the live CD and get the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") results.

You can also try booting in recovery mode. But if it hangs don't hard reboot, try the safe reboot [Alt+SysRq R-E-I-S-U-B]("http://en.wikipedia.org/wiki/Magic_SysRq_key#Uses")

---

### Post by kindlykokokat on 2012-11-28
how quickly should the R-E-I-S-U-B series be pressed?

---

### Post by bcbc on 2012-11-28
I normally just pause a little after each one. Sometimes you get visual feedback as it proceeds, e.g. remounting partitions read-only, other times there's no feedback until the last one that reboots the computer.
If it doesn't work then you don't have any option but to hard reboot.

(You hold down Alt + SysRq while pressing the other keys)

---

### Post by kindlykokokat on 2012-11-28
> **bcbc said:**
> 

You can also try booting in recovery mode. 

Is this with the live cd?

---

### Post by kindlykokokat on 2012-11-28
here is the result

```
  

                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   409,602,047   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda2         409,602,048   976,771,071   567,169,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A030F41930F3F3DE                       ntfs       Primary HDD
/dev/sda2        78E8C3E7E8C3A22C                       ntfs       Storage HDD
/dev/sdb1        B82D-B486                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/B82D-B486         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)







```

---

### Post by bcbc on 2012-11-28
It looks like the root.disk is corrupted:
```
sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

When this happens there is a risk of loss. The best approach is to run chkdsk from Windows, and then confirm the root.disk is still there, or attempt to recover it (sometimes chkdsk will move it to a \found.000 folder).

Then if it's still corrupt, you can fsck it from a live CD.

Here is a guide with pics and step by step for the chkdsk bits: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html) (even though your root.disk isn't missing, I'd be hesitant to try fsck'ing it if there is a chance of ntfs corruption, so I recommend chkdsk first).

---

### Post by kindlykokokat on 2012-11-28
> **bcbc said:**
> and then confirm the root.disk is still there, or attempt to recover it (sometimes chkdsk will move it to a \found.000 folder).



How do I do this?

---

### Post by bcbc on 2012-11-28
That link describes how to run chkdsk and how to find it if it's moved.

---

### Post by kindlykokokat on 2012-11-28
I ran checkdisk, it found no error.

I checked in the ubuntu folder and the root.disk is there.

---

### Post by bcbc on 2012-11-29
Okay so if it still doesn't boot you can try fsck'ing the root.disk. Boot from that Ubuntu CD, and drop to a shell (Ctrl+Alt+T):
```
sudo mount /dev/sda1 /mnt
sudo fsck /mnt/ubuntu/disks/root.disk
sudo umount /mnt
sudo reboot

```

Commands explanation:
1. mount /dev/sda1 partition that contains the root.disk
2. fsck the root.disk
3. unmount /dev/sda1
4. reboot the computer and see if it works

---

### Post by kindlykokokat on 2012-11-29
i did as you asked. fsck finished very quickly, it took less than 1s. it said everything was fine and listed how many files there are.

---

### Post by kindlykokokat on 2012-11-29
I still can not get into ubuntu, it has the same problem, stuck at a reddish screen.

---

### Post by bcbc on 2012-11-29
If you run the bootinfoscript again and it still shows that the root.disk is corrupted, re-run the fsck but this time force it by adding -f to the command, and v means verbose output:
```
sudo mount /dev/sda1 /mnt
sudo fsck -fv /mnt/ubuntu/disks/root.disk
sudo umount /mnt
```

You can try booting in recovery mode as well... if you see a grub menu, depending on the version of grub, the second entry may say recovery mode. Select that.
If you don't see recovery mode, but rather 'Advanced options', then select that and then select the recovery mode (second entry).

If you don't see a grub menu, then hold the SHIFT key immediately after selecting Ubuntu.

---

### Post by kindlykokokat on 2012-11-29
I looked in fsck man page and there is no -f option?

---

### Post by bcbc on 2012-11-29
Manpage entry for fsck:
> In  actuality,  fsck  is simply a front-end for the various file system
       checkers (fsck.fstype) available under Linux.  The file system-specific
       checker  is  searched for in /sbin first, then in /etc/fs and /etc, and
       finally in the directories listed in  the  PATH  environment  variable.
       Please  see  the  file system-specific checker manual pages for further
       details.

Manpage entry for [fsck.ext4]("http://manpages.ubuntu.com/manpages/precise/en/man8/fsck.ext2.8.html"):
> -f     Force checking even if the file system seems clean.

---

### Post by kindlykokokat on 2012-11-29
```
fsck from util-linux-ng 2.17.2
e2fsck 1.41.14 (22-Dec-2010)
/mnt/ubuntu/disks/root.disk: recovering journal
Clearing orphaned inode 524560 (uid=118, gid=131, mode=0100600, size=0)
Clearing orphaned inode 523857 (uid=118, gid=131, mode=0100600, size=0)
Clearing orphaned inode 523848 (uid=118, gid=131, mode=0100600, size=0)
Clearing orphaned inode 523843 (uid=118, gid=131, mode=0100600, size=0)
Clearing orphaned inode 523841 (uid=118, gid=131, mode=0100600, size=0)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/mnt/ubuntu/disks/root.disk: ***** FILE SYSTEM WAS MODIFIED *****

  941211 inodes used (59.34%)
    2440 non-contiguous files (0.3%)
    1058 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 872264/985
 5729331 blocks used (90.45%)
       0 bad blocks
       1 large file

  715264 regular files
  132561 directories
      57 character device files
      25 block device files
       1 fifo
      62 links
   93293 symbolic links (67868 fast symbolic links)
       1 socket
--------
  941264 files


```

---

### Post by kindlykokokat on 2012-11-29
....

---

### Post by bcbc on 2012-11-29
So it still doesn't boot? How about a refreshed bootinfoscript?

I'll check back in the morning - my day is pretty much done.

---

### Post by kindlykokokat on 2012-11-29
this is the new result. i think it's the same as before.

still can't boot, although this time the ubuntu logo came up before it hangs, although I suspect this is just random.

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files:        /grldr /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /grldr /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk

sda1/Wubi: _____________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048   409,602,047   409,600,000   7 NTFS / exFAT / HPFS
/dev/sda2         409,602,048   976,771,071   567,169,024   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 4004 MB, 4004511744 bytes
116 heads, 51 sectors/track, 1322 cylinders, total 7821312 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1                  32     7,821,311     7,821,280   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        A030F41930F3F3DE                       ntfs       Primary HDD
/dev/sda2        78E8C3E7E8C3A22C                       ntfs       Storage HDD
/dev/sdb1        B82D-B486                              vfat       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/B82D-B486         vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)




```

---

### Post by bcbc on 2012-11-29
When you ran chkdsk did it tell you to reboot your computer and did you do that and see it run to completion (stages 1 to 3 and/or stage 4 if you selected to check for bad blocks?).

---

### Post by kindlykokokat on 2012-11-30
I didn't reboot. I ran chkdsk from a command prompt and it didn't ask me to restart.

---

### Post by bcbc on 2012-11-30
That's your C: drive so it's not possible for chkdsk to run from a command prompt. It can run from a Windows repair CD prompt, otherwise you have to reboot.

---

### Post by kindlykokokat on 2012-11-30
How do i get vista to restart and chkdsk?

---

### Post by bcbc on 2012-11-30
There were instructions and screen shots in that link I provided: [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

I wanted you to run chkdsk prior to doing the fsck. I believe there's more risk if you do it the other way around. I'm not particularly optimistic given that fsck thought that the file system was clean, found something when you forced it, and then it was still corrupted. 

But hopefully it is still recoverable. Unfortunately not every corrupted root.disk is recoverable.

---

### Post by kindlykokokat on 2012-11-30
ok i did a chkdsk at boot after a restart, it says nothing is wrong.

i still can't get into ubuntu :(

---

### Post by bcbc on 2012-11-30
What bothers me is that the bootinfoscript cannot mount it, yet somehow grub can read the grub menu (other wise you'd get a grub prompt), and when you ran fsck it apparently fixed it. So I'd try that again. 

Boot the live CD and first try to mount it:
```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt

```

See if it spits out an error. If it does, try to fsck again (the first line is to ensure it's not mounted - if it isn't it will spit out an error but do it anyway):
```
sudo umount /mnt
sudo fsck /media/win/ubuntu/disks/root.disk
```

Report back. If you managed to mount it, instead of fsck'ing please unmount it and then run the bootinfoscript again - this is required to see the grub boot entries on the disk.

---

### Post by kindlykokokat on 2012-12-01
sorry haven't been updating because of the weekend.

anyway i tried pressing shift right after i selected ubuntu in the windows boot menu and i got into grub and when i chose the kernel, i could get into ubuntu. the default boot is a pae but it had never worked so i always choose the additional option then the latest kernel.

normally when i choose ubuntu from the windows boot menu, it will get into grub automatically.

I still can not get into ubuntu without using shift after the windows boot menu.

Maybe this additional information would be helpful to you?

---

### Post by kindlykokokat on 2012-12-01
btw I haven't tried post#29 yet since I think the information in #30 might be relevant.

---

### Post by bcbc on 2012-12-02
Before the grub menu always used to show, but in recent versions of grub it suppresses the grub menu for Wubi.

So that's normal. You have to hold down the Shift key to see the menu.

---

### Post by kindlykokokat on 2012-12-03
> **bcbc said:**
> Before the grub menu always used to show, but in recent versions of grub it suppresses the grub menu for Wubi.

So that's normal. You have to hold down the Shift key to see the menu.

ok then some quick questions

1. is the problem then just grub automatically loading a pae version of the kernel, which i have known to cause it to fail to load?

2. what about the bootinfoscript saying something about being unable to mount?

3. how do i change the setting of grub to a) load the non pae version by default b) show the grub menu on boot

I presume this meant that a very recent grub update changed the setting? as in last week update?

---

### Post by bcbc on 2012-12-03
> **kindlykokokat said:**
> ok then some quick questions

1. is the problem then just grub automatically loading a pae version of the kernel, which i have known to cause it to fail to load?

2. what about the bootinfoscript saying something about being unable to mount?

3. how do i change the setting of grub to a) load the non pae version by default b) show the grub menu on boot

I presume this meant that a very recent grub update changed the setting? as in last week update?

1. What release did you upgrade to? For 12.10 they no longer ship a non-pae kernel. Otherwise I'm confused why you would have a mix of kernels?
2. Exactly. I'm confused about that too.
3. You can either uninstall the kernel that doesn't work or use something like the grub-customizer to specify which menu entry to boot.
(4.) I'm not sure whether it was a release-specific grub-update that started suppressing Grub menus for Wubi installs, or a general update. I know that since 12.04 (and maybe 11.10) it stopped adding the Windows entries to Grub (which causes it to autohide since it only detects one OS). Most of the time I boot the default entry anyway - so it doesn't bother me. If you fix your default then it probably won't bother you either. But you can use the grub-customizer to make it always show.

---

### Post by kindlykokokat on 2012-12-03
> **bcbc said:**
> 1. What release did you upgrade to? For 12.10 they no longer ship a non-pae kernel. Otherwise I'm confused why you would have a mix of kernels?
2. Exactly. I'm confused about that too.
3. You can either uninstall the kernel that doesn't work or use something like the grub-customizer to specify which menu entry to boot.
(4.) I'm not sure whether it was a release-specific grub-update that started suppressing Grub menus for Wubi installs, or a general update. I know that since 12.04 (and maybe 11.10) it stopped adding the Windows entries to Grub (which causes it to autohide since it only detects one OS). Most of the time I boot the default entry anyway - so it doesn't bother me. If you fix your default then it probably won't bother you either. But you can use the grub-customizer to make it always show.

1. im using 11.10 i havent been updating because last time i updated version it caused the install to not boot. i don't know why i have a mix of kernel but it used to be everytime i boot i would get a grub menu with 3 options pae pae-recovery and additional options, which if selected i would have a list of pretty much every kernel version since the first install

4. i never have windows in my grub menu, it has always been just a list of different kernel version (although im only about 90% sure on this).

---

### Post by oldfred on 2012-12-03
A couple of questions or comments.

I do not know wubi and bcbc does.

But if you really like Ubuntu why have you not converted to a full partitioned install. Even the developer of wubi expects you to convert.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
And with a core2 system, pae is not an issue. If anything you probably should be using the 64 bit version if you have 3GB or more of RAM. 
The issue may be whether dpkg correctly is adding the nVidia drivers back into your kernel when you add the nVidia drivers??

---

### Post by kindlykokokat on 2012-12-04
> **oldfred said:**
> A couple of questions or comments.

I do not know wubi and bcbc does.

But if you really like Ubuntu why have you not converted to a full partitioned install. Even the developer of wubi expects you to convert.

       From the developer of wubi:
[http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/](http://howsoftwareisbuilt.com/2009/03/12/interview-with-agostino-russo-wubi-ubuntu/)
Agostino: Wubi actually wasn’t designed to do long-term installations. The main aim was really to let people try out Ubuntu with confidence. Normally, users that start with Wubi tend to upgrade to a full installation to a dedicated partition at the next release cycle.

    
And with a core2 system, pae is not an issue. If anything you probably should be using the 64 bit version if you have 3GB or more of RAM. 
The issue may be whether dpkg correctly is adding the nVidia drivers back into your kernel when you add the nVidia drivers??

i could get into ubuntu using a shift to get the grub menu so i don't think its the nvidia drivers.

---

### Post by bcbc on 2012-12-04
You can just dump some data to a text file instead of running bootinfoscript, for example:

```
ls -al /boot >> ~/bootdata.txt
cat /boot/grub/grub.cfg >> ~/bootdata.txt
cat /etc/fstab >> ~/bootdata.txt
cat /etc/default/grub >> ~/bootdata.txt
df -h >> ~/bootdata.txt
sudo fdisk -l >> ~/bootdata.txt
sudo blkid >> ~/bootdata.txt
gedit ~/bootdata.txt

```
Then copy and paste the contents here.

---

