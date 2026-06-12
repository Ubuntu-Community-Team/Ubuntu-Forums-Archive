---
title: "Grub Error 17"
date: 2007-04-16
forum: General Help
---

### Post by Joseph Elliott on 2007-04-16
Big problems, i came home from work today only to find my computer has decided not to work.  I was downloading an avi file with bittorrent last night and it was still downloading this morning so I left it to continue.  I got home and my comp wouldn't respond.  I manually restarted and it said "loading grub" then "error 17".  I have no idea what happened.

here data on my hard drive:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       30332   243641758+  83  Linux
/dev/hda2           30333       30401      554242+   5  Extended
/dev/hda5           30333       30401      554211   82  Linux swap / Solaris


I dont know how to get a menu.lst

can anyone help me?

---

### Post by computerease on 2007-04-16
See [http://ubuntuforums.org/showthread.php?p=1152935](http://ubuntuforums.org/showthread.php?p=1152935)

---

### Post by m.musashi on 2007-04-16
That error usually shows up when GRUB can't read the /boot files. This could be because the partitions changed (so hda2 had the /boot files but that partition is now hda3 because you made some changes) or because there are problems with the file system or files. Trouble shooting this can be a pain.

The menu.lst is located in /boot/grub/menu.lst. If you have a live CD around (and you probably do if you installed it yourself at it's the same CD) boot from it and you should be able to open that file and post its contents here. Perhaps someone can help you troubleshoot the problem.

The other option is to just have GRUB rebuild itself. I don't remember the steps offhand but it can be done from a live CD. I'll try and find them and post back.

EDIT: okay, I found a thread with the steps [here](http://ubuntuforums.org/showpost.php?p=1654511&postcount=18). This will rebuild GRUB and may solve your problem. If not, you might have some disk/data corruption. Hopefully that isn't the case.

---

### Post by Joseph Elliott on 2007-04-16
thanks computerease but reformatting isn't an option.  I have extremely important files that I was working on late last night and forgot to back up before I went to bed.  I tried sudo grub, then find /boot/grub/stage1 but it said the file doesnt exist.

whats the command to open /boot/grub/menu.lst?

---

### Post by m.musashi on 2007-04-16
I wasn't suggesting you reformat. Only that you rebuild GRUB. That would not make any changes to your partitions except the MBR. Of course, if you have important files you should back them up before making any changes. You can never be sure that things will go as planned.

The link I gave should help you repair GRUB.

As for opening menu.lst, you can just navigate there in nautilus (places -> file system) and double click it. You won't be able to make changes but if you just want to see it that is fine. If you want to edit it do
```
sudo gedit /boot/grub/menu.lst
```

EDIT: if stage1 doesn't exist I'm not sure what that means. My first guess is that it's not good news. You can find it yourself by looking in the /boot/grub directory.

---

### Post by Joseph Elliott on 2007-04-17
sudo gedit /boot/grub/menu.lst

opens a blank notepad,  whats my next step?

---

### Post by m.musashi on 2007-04-17
If you are working from a live CD you might have to mount the root partition to actually see it or use it. I thought that happens automatically with a live CD but I could be wrong. There is probably a terminal command to check what partitions are mounted but I don't think I know one.

One way to check is use nautilus (places -> computer and then open filesystem) to navigate to the /boot directory and see what's there? You may need to click view and select show hidden files to see the contents of the directory. If you can't get to this directory you may need to mount the partition. Mounting might also solve the problem of trying to edit menu.lst. I'm doing this from memory but I think to mount it you need to do this:
```
sudo mkdir /mnt/name_you_choose
sudo mount /dev/hda1 /mnt/name_you_choose
```
Change hda1 to match your root partition.

If it is already mounted and both the stage1 and menu.lst missing then I think you might have larger problems. If the partition is mounted, can you see what sort of files are there? Posting a screen shot might make it easier to describe.

Without knowing the exact situation it's hard to advise. However, if it were me, I would probably backup everything important and reinstall. Of course, if it's just a matter of mounting the partition then maybe it will be easy to fix.

EDIT: I'm attaching a couple screen shots of my /boot and /boot/grub directories. I have feisty and have saved a few backup files but other than that there should be some similarities to your directories - especially things like menu.lst, stage1 in the /boot/grub dir. If you are missing these then they either need to be reinstalled or if the cause is corruption further investigation and probably a reinstall. You will also want to try and track down the cause of corruption if that is the case.

---

### Post by Joseph Elliott on 2007-04-18
ubuntu@ubuntu:~$ sudo mkdir /mnt/harddrive
ubuntu@ubuntu:~$ sudo mount /dev/hda1 /mnt/harddrive
mount: you must specify the filesystem type
ubuntu@ubuntu:~$


I checked in Disks Manager and it says that the partition exists but isn't formatted.  The boot directory only holds 6 files(abi-2.6.15-23-386, config-2.6.15-23-386, initrd.img-2.6.15-23-386, memtest86+.bin, System.map-2.6.15-23-386, vmlinuz-2.6.15-23-386) and there doesn't seem to be a grub anywhere.

---

### Post by m.musashi on 2007-04-18
This is sounding more and more like a corrupt file system. I've never had to specify the file system type for a Linux partiton. It's possible that it can't mount it because it doen't recognize it. To specify the type for an ext3 fs do
```
sudo mount -t ext3 /dev/hda1 /mnt/harddrive
```
At this point, I'm pretty much out of ideas. If you can get it to mount using the above, you could try and replace the /boot/grub dir but I'm not exactly sure how to do that. You might also check [this thread](http://ubuntuforums.org/showpost.php?p=2467946&postcount=4). The cfdisk might allow you fix the file system type if it won't mount.

---

### Post by Joseph Elliott on 2007-04-18
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/harddrive
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$

---

### Post by m.musashi on 2007-04-18
Try the cfdisk bit in the thread I linked. If that doesn't fix it I'd say you might be out of luck. If it doesn't recognize the partition as ext3 (and it should be if you did a defult install) then that implies problems with the fs or disk. As I understand it, cfdisk will change the type identifier but not alter the contents of the disk (read the last post in that thread). However, it seems that Linux doesn't really care about that so it may not have any effect. I don't really know much about cfdisk.

Since I think you have more a drive or file system problem rather than a grub problem (although you will still need to get grub to work if you can fix the  fs problem), you can try starting a new thread about the inability to mount the partition and maybe someone can offer better advice.

---

### Post by Abcd1978 on 2008-05-04
im sry this may be somewhat off subject,but can someone tell me how to fix a GRUB Error 17 for kubuntu? plz describe easily,because i not very good with all this parcel and boot stuff.:(

---

### Post by smo0th on 2008-05-17
> **Abcd1978 said:**
> im sry this may be somewhat off subject,but can someone tell me how to fix a GRUB Error 17 for kubuntu? plz describe easily,because i not very good with all this parcel and boot stuff.:(

kubuntu should use the same GRUB structure as ubuntu

---

### Post by smo0th on 2008-05-19
> **Joseph Elliott said:**
> ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/hda1 /mnt/harddrive
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

ubuntu@ubuntu:~$

At this point I'm sure something went wrong and messed up your file/disk structure(probably a recent update), please try the following:

1. Boot from a live cd.
2. Open a terminal and type:
```
sudo e2fsck -C0 -p -v -f /dev/hda1
```
if that doesn't work try ```
sudo e2fsck -C0 -v -f /dev/hda1
```
3. If you go with the second option, read carefully the first 10 lines before answering, just make sure you don't change ext3 file system for ext2 and stuff like that. After those lines you should proceed with the default(y) option to fix the errors, a ton of errors could arise here so be patient and bare with it.
4. Run this several times until you get no errors.
5. Reboot your system and check if you are able to boot normally.

If you are able to boot, enjoy!

If you are not able to boot, run the live cd again and do the following:
```
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 /media/ubuntu
cd /media/ubuntu/boot/grub
ls
```

Now, you should see some files, copy what you have in 'menu.lst' and 'device.map' so I can help you further.

---

