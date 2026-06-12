---
title: "Add Linux To Boot.ini"
date: 2008-05-25
forum: General Help
---

### Post by Reg Editor on 2008-05-25
Hello. I have XP installed on each of 2 partitions,plus Ubuntu and Mint.
The last time I reinstalled Windows,I used a command that restored the Mint bootloader.
This time I have been trying to get to the Mint bootloader via Microsoft&#8217;s boot loader.When I select Linux and press enter,the screen changes to a cursor near the top left.
Ubuntu was installed before Mint.
Mint is on /dev/hda9 

I used the  method shown below


f) Edit boot.ini, adding the line 
 C:\BOOTSECT.LNX=linux
at the end, and rehide the file 
 attrib +h +s +r \boot.ini


Q:      Why is it that the more accuracy you demand from an interpolation
        function, the more expensive it becomes to compute?
A:      That's the Law of Spline Demand.
owner@owner-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda9              4799024   2620620   1934620  58% /
varrun                  225280       100    225180   1% /var/run
varlock                 225280         0    225280   0% /var/lock
udev                    225280        76    225204   1% /dev
devshm                  225280         0    225280   0% /dev/shm
lrm                     225280     34696    190584  16% /lib/modules/2.6.22-14-generic/volatile
/dev/hda1             22531128  20372840   2158288  91% /media/hda1
/dev/hda7              4806904   2094896   2467824  46% /media/hda7
fusesmb                4799024   2620620   1934620  58% /home/owner/Network
/dev/hdc                  4090      4090         0 100% /media/cdrom1
owner@owner-desktop:~$ dd if=/dev/hda9 of=/bootsect.lnx bs=512 count=1
dd: opening `/dev/hda9': Permission denied
owner@owner-desktop:~$ sudo dd if=/dev/hda9 of=/bootsect.lnx bs=512 count=1
[sudo] password for owner:
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00936318 seconds, 54.7 kB/s
owner@owner-desktop:~$ 


-------------------------------------------------------------------



Once you run this command, you will have bootsect.lnx file in "/" (root) directory.

5. Mount a DOS formatted disk. Type:
mount -t msdos /dev/fd0 /mnt

6. Copy the bootsect.lnx file to the diskette:
cp /bootsect.lnx /mnt

7. Boot up to W2k/XP (by removing the Linux boot disk).

8. After booting up to W2k/XP, insert the DOS disk, and copy the file A:\bootsect.lnx to C:\ drive.


I've also used BootPart and got the same result.

All help appreciated

---

### Post by pixel :-) on 2008-05-25
What you are complitly cut out from the linuxes?

Try this as a temporary quick fix,easy and quick [http://gag.sourceforge.net/]("http://gag.sourceforge.net/")

You absolutely need to boot from the windows bootloader?I know thers a utility that permits that, try this [http://http://users.bigpond.net.au/hermanzone/p9.html]("http://http://users.bigpond.net.au/hermanzone/p9.html")

Whats wrong with grub?

---

### Post by Reg Editor on 2008-05-25
Thank you.I'm using SuperGrub on a CD to boot Mint.
I prefer the Mint boot loader as it has an image like the Desktop background,so intend to go back to that in a while.
But I'm determined to get the boot.ini method to work first,it has become a challenge.:)

---

### Post by meierfra. on 2008-05-25
Is grub installed to the boot sector of  /dev/hda9 ?

If not, do this

```
sudo grub
```

and at the grub prompt:

```
root (hd0,8)
setup (hd0,8)
quit
```


and try again.

---

### Post by pixel :-) on 2008-05-25
don't you whant to try the WinGrub method?

---

### Post by Reg Editor on 2008-05-25
What do I need to do to check if grub installed to the boot sector of /dev/hda9 ?

Although it must be as SuperGrub takes me to the same Mint boot options as before I reinstalled XP.

---

### Post by Reg Editor on 2008-05-25
GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>


    GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]


The smilies are supposed to be 8's

grub> root (hd0,8)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0,8)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,8)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,8)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,8) /boot/grub/stage2 p /boot/grub/menu
.lst "... succeeded
Done.

grub>

---

### Post by meierfra. on 2008-05-25
O.K you now have grub installed in the right place. Just try the whole procedure (which you outlined in your first post) again. (Of course you don't need to edit boot.ini again)

---

### Post by Reg Editor on 2008-05-25
Will the existing bootsect.lnx be overwritten.I've been trying to delete it,but don't know how to change directory without the location..When I right click and click on properties on a folder or file in "File System" ,the volume and location aren't shown,just blank

I think "File System" is hda9,it wasn't always like this I think

---

### Post by meierfra. on 2008-05-25
Yes "dd" will automatically overwrite the file.

You should also be able to  delete it with

```
sudo rm /bootsect.lnx
```

---

### Post by Reg Editor on 2008-05-25
Thanks meierfra.The grub commands you gave have got it working.:)
Will you explain it to me as I would like to understand.Why was it
root (hd0,8)
setup (hd0,8)instead of 9?

Again the smilies should be 8's

---

### Post by meierfra. on 2008-05-25
Grubs start counting at zero. So (hd0,8[SIZE="1"] [/SIZE]) means the 9th partition on the first hard drive.

---

### Post by Reg Editor on 2008-05-25
Thanks,I had read that somewhere and forgotten it.The 1st method I tried was BootPart.Could copying or trying to copy the boot sector data have corrupted it?

---

### Post by meierfra. on 2008-05-26
I doubt it. It's just that by  default Ubuntu installs grub to  the MBR of the first hard drive and not to the boot sector of its partition.

---

### Post by Reg Editor on 2008-05-26
You should write a guide: How To Add Linux To Boot.ini After Windows Is Reinstalled.:)

Thanks again.

---

### Post by adrian15 on 2008-05-27
> **Reg Editor said:**
> You should write a guide: How To Add Linux To Boot.ini After Windows Is Reinstalled.:)

Thanks again.

I wrote one howto about it myself: [How to boot Grub from Windows](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows).

Enjoy it!

adrian15

---

### Post by emsee_bristol on 2008-07-26
I want to add Ubuntu to boot.ini but dispite reading the messages in this thread and others I can't seem to get it to work.

I don't want to replace my MBR or keep alterering the BIOS to change the boot drive - editing boot.ini seemed the far simplest and least distructive method - at least that's what I thought when I started but it seems a lot more complicated than it should be ](*,)

I've got 2 SATA drives, the first one has Win XP on it (2 partitions) and the second one is new & I want install Ubuntu onto it.

This is what I've done so far:
[LIST=1]
[*]Boot from Ubuntu CD & run live trial
[*]Double-click the 'Install' icon to start the installation
[*]Partition new drive to main & swap partitions
[*]On the last setup screen, change the GRUB installation to the Ubuntu drive (*\dev\sdc1* in my case) (the partitioning utility didn't see my floppy drive)
[*]After installation has finished, click 'Continue using live CD'
[*]Click Applications - Accessories > Terminal
[*]Type: **sudo su**
[*]Type: **dd if=/dev/sdc1 of=bootsect.lnx bs=512 count=1**
[*]Click Places - Home folder
[*]Drag & drop bootsect.lnx onto a USB pendrive
[*]Reboot into Windows (removing CD when prompted)
[*]Copy bootsect.lnx from USB pendrive to C:\
[*]Edit boot.ini & add **c:\bootsect.lnx="Ubuntu Linux"** after the line for Windows
[/LIST]

After rebooting & choosing the Ubunto option on reboot, I get **GRUB** displayed in the top left along with a flashing cursor and nothing more happens.

I have tried running Wubi but it only gives me the option of installing to my C drive which I don't want (although the new Ubuntu drive isn't visible under Windows anyway).


Can anyone help before I loose Patience and give up on Linux? :frown:
Should I save the file as linux.bin (instead of bootsect.lnx) as shown in the Classical Final Solution section of adrian15's [howto]("http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows")?

---

### Post by adrian15 on 2008-08-11
> **emsee_bristol said:**
> 
Can anyone help before I loose Patience and give up on Linux? :frown:
Should I save the file as linux.bin (instead of bootsect.lnx) as shown in the Classical Final Solution section of adrian15's [howto]("http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows")?
Please check:
[http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows#Classical_solution](http://www.supergrubdisk.org/wiki/Howto_Boot_Grub_from_windows#Classical_solution)
That **Windows Chainloads Grub** option does something that Ubuntu installation does not do and that will let you chainload Linux from Windows' boot.ini **even if Linux is on a second hard disk**!

:)

adrian15

---

