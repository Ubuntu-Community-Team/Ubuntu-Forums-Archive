---
title: "qtparted not finding drives"
date: 2008-03-10
forum: General Help
---

### Post by KMJones1 on 2008-03-10
I have a mcahine with Ubuntu safely installed on /dev/hdc and an unformatted /dev/sda.
Info looks OK:

sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/hdc: 6448 MB, 6448619520 bytes
255 heads, 63 sectors/track, 784 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1         747     6000246   83  Linux
/dev/hdc2             748         784      297202+   5  Extended
/dev/hdc5             748         784      297171   82  Linux swap / Solaris
 
I tried to use qtparted to format the sda drive but it fails to find either drive:

sudo qtparted
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

How can I get this thing partitioned?
:confused:

---

### Post by kuja on 2008-03-10
Well, there's a handful of ways. parted, fdisk, cfdisk, gparted, and I'm sure there are more, but those are the ways I've done it before.

Here's how to do it with parted  (in a shell, though)

```
sudo parted /dev/sda
```

some of the commands:

"print" - show the partition table
"mklabel" create the partition table (you'll probably want to use the "dos" partition table, here)
"mkpartfs" - create a partition and format it with any partition format that parted can do. (You can express the size when creating in MB or GB (ie; 10.1GB)  - however, I think it's in decimal (ie: 1kb = 1000 bytes), not binary (ie: 1kb = 1024bytes) like you might expect, use iB to get it to take it in binary IIRC (ie: 10.1GiB)
"help" - print help info

---

### Post by Prefader on 2008-03-10
Those errors are related to non-existent input devices configured in xorg.conf, not your drives - check your xorg.conf for entries related to wacom devices.

---

### Post by KMJones1 on 2008-03-10
Thanks for this.
In the meantime I have discovered parted and managed to get a partition on it that way (as you have suggested above!).

Now I get the qtparted error message BUT it runs and shows the two drives with partition info!

However, I cannot see any way to amend a partition in qtparted (e.g. size, label, hidden).

---

### Post by monte48lowes on 2008-03-10
I recommend using gparted vice qtparted. I have always had better luck.


Mike

---

### Post by KMJones1 on 2008-03-10
That last was for kuja.

Prefader: I don't seem to have that file, at least search of "file system" doesn't produce it.

---

### Post by KMJones1 on 2008-03-10
Monte48lowes: that was a brilliant suggestion; gparted seems to have worked.
Many thanks. Pity qtparted seems to have been chosen as the default Ubuntu partition manager.

---

### Post by Prefader on 2008-03-10
/etc/X11/xorg.conf

---

### Post by KMJones1 on 2008-03-10
Thanks prefader- found the file and commented out 3 wacom sections, but still the same error messages and qtparted opening OK. 
It now shows the new partition and all the controls now. Making progress!

---

### Post by Prefader on 2008-03-10
There's more than just the 3 "InputDevice" sections . . . look for additional entries in the "SeverLayout" section of the file.  You don't want to remove the entire "ServerLayout" section (bad!), just the 3 lines that refer to the wacom devices.  Mine looks like this (yours will probably be similar):

```

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "Synaptics Touchpad"
        Option "AIGLX" "true"
EndSection

```

Basically, just remove any InputDevice lines that reference devices you don't actually have.

You will then need to restart your X server - either reboot, or close all open apps and hit CTRL-ALT-BACKSPACE.

---

### Post by kuja on 2008-03-10
> **KMJones1 said:**
> Thanks for this.
In the meantime I have discovered parted and managed to get a partition on it that way (as you have suggested above!).

Now I get the qtparted error message BUT it runs and shows the two drives with partition info!

However, I cannot see any way to amend a partition in qtparted (e.g. size, label, hidden).

I don't think it can change the label (a drawback for sure  - though in an otherwise solid piece of partitioning software), but to change the size you can use "resize", and to make it hidden you use the "set" command.
edit: oops, forgot, no wonder I couldn't find anything to do with label, it calls it name! silly me - then again, parted says dos disklabels don't support partition names :s - You could however opt to set the label via the filesystem with a program like e2label or xfs_admin.

---

### Post by KMJones1 on 2008-03-10
prefader: 
I just rebooted and have a major problem. It doesn't reach the login screen, but shows a DOS screen "Failed to start X server........." On asking for info I get various items, including: 
"Data incomplete in file /etc/x11/xorg.conf
Undefined input devide "stylus"referenced by server layout
Problem parsing config file
Error parsing config file"
then leaves me in DOS screen with "Server login:"

I tried to run gedit to correct the file but it won't run.
Any help please?

---

### Post by Prefader on 2008-03-10
You're getting this error because you didn't clean up the "ServerLayout" section.  Have a look at the last post I made here for an example of what yours should look like.

"gedit" is a graphical application - it only works if there's an X server running.  Try
```
sudo nano /etc/X11/xorg.conf
```
When you're done editing the file, hit CTRL-O to write your changes, then CTRL-X to exit.

If all else fails, post the contents of your xorg.conf file here and I'll clean it up for you.  Sorry if I got ahead of you, I didn't mean to!

---

### Post by KMJones1 on 2008-03-10
Many thanks but I beat you to it!
I looked at the files in X11 and noticed a backup version of xorg.conf so did a rename and reboot and am back on the air.Whew!
Now I'll go back to your earlier advice and try again.

---

### Post by KMJones1 on 2008-03-10
I have now amended the xorg file as suggested and all looks good (qtparted opens without errors).

So I now have a system drive  (/dev/hdc - a small 6.5GB drive) with Ubuntu on it, and a 120GB drive (/dev/sda with single Fat32 partition because I want WinXP machines to use it). The question is how do I get some files onto this second drive. File browser only seems to see the small system drive. Is this all about mounting? The help files are no help on that!

---

### Post by kuja on 2008-03-10
try something liket his perhaps?

```
sudo mkdir /media/sda1
sudo mount -t vfat  -o utf8 -o rw -o gid=1000 -o uid=1000 -o dmask=0750 -o fmask=0640 /dev/sda1 /media/sda1
```

(I'm not quite sure about everything here, I don't play with vfat too often, but I assume this should do the trick)
If it works --

```
sudo su -c 'echo "/dev/sda1 /media/sda1 vfat rw,utf8,user,uid=1000,gid=1000,dmask=0750,fmask=0640 0 0">> /etc/fstab'
```

---

### Post by KMJones1 on 2008-03-11
kuja - that was great - thanks. We are getting somewhere but not finished yet.

Now I can see the drive as /media/sda1 in file browser, but marked with a red box and cross.
I can see the Windows computer files from network browser.
I can move files into /media/sda1 from the Windows computer, but cannot delete them (no permission).
I CANNOT see the files in sda1 from the Ubuntu file browser and cannot set permissions (selcting Properties the three drop down lists won't accept any permission for read/write, etc.).
There seems to be a permission difficulty; how do I deal with this please?
:confused:

---

### Post by KMJones1 on 2008-03-11
Further to the last - I can see the files in the network at:  smb://server/files (server is name of computer), but have no idea where they actually are since they don't appear in the file browser.
Permission for the drive folder  /media/sda1 is shown as 025.
Folders within //server/files permission is 555, and files have permission 554. I can't change these, even by editing smb.conf share definitions to 0777.
I've tried "sudo chmod 777 files" and "sudo chmod 777 /media/sda1 " to no effect.
It shouldn't be this difficult surely!!

---

### Post by kuja on 2008-03-11
With the setup I gave above, it should be accessible as uid Y gid 1000 (default in ubuntu for first user) ..... can you see the files as root??
ie: sudo ls -l /media/sda1
Perhaps loosening up the permissions would help --
In the file /etc/fstab, edit the (probably) last line, that was just added recently.
Where it says gid, change it to 100 (from 1000)
Where it says dmask, change it to 0777
Where it says fmask, change it to 0666

Save,then umount and mount the partition again and see if it works

---

### Post by KMJones1 on 2008-03-11
Thanks for more help!

The ls -l /media/sda1 produces (kev is my user name):
total 80
---x-wxrwx 1 kev kev 60137 2003-04-13 14:54 appA.html (this is one of my files)
d----w-rwx 3 kev kev 16384 2008-03-11 09:21 Books (this is a directory of my files)

I amended fstab as suggested and did sudo umount /media/sda1 and get:
    only root can unmount /dev/sda1 from /media/sda1

Any other options?

PS I am about to go out for the evening, and will be out most of tomorrow.

---

### Post by KMJones1 on 2008-03-11
Just found -l switch in umount works.
"sudo umount -l /media/sda1! worked and without remounting left me with /media/sda1 with permissions 1200755 and owner root.  I cannot make folders in it.
Then "sudo mount /media/sda1" gives me the folder as before with red box, permission 027 and me as owner.

---

### Post by kuja on 2008-03-11
I'm at a loss for why it won't behave. Try removing the dmask and fmask options and remount to see if it behaves any better. Also try doing "sudo chown kev:kev /media/sda1". Why use an antiquated system like FAT when there's an ext2 driver for windows anyhow?

---

### Post by KMJones1 on 2008-03-12
Thanks Kuja - sorry to be a pain.
Removing the dmask and fmask makes no difference.
The chown operation was not permitted. The current state is permissions 000, owner kev.

Since this drive is still unused I'll try a reformat. I only chose Fat because I thought there was a problem with Windows reading other formats. I'll try ext2 as suggested. I've commented-out the line in fstab relating to it. Anything else I should change before reformatting?
many thanks for your help!

---

### Post by kuja on 2008-03-12
Should be worth a try. I think you can use ext3, just the windows driver won't take advantage of the ext3 journal (which is the primary difference between ext2 and ext3). [http://www.fs-driver.org/](http://www.fs-driver.org/) - that should be where you get the driver at. I expect it'll be easier to manage than fat (in addtion to be more efficient, faster, more resistant to corruption, and not subject to the limitations of fat (like the 4GiB filesize limit))

---

### Post by KMJones1 on 2008-03-12
Thanks kuja.
Definitley making progress. 
Somehow I managed to remove the /media/sda1 folder, then refomatted as ext3 OK.
I now have a folder "/filestore" with permission 1200755 and owner root. 
I can make folders in it but have to use "sudo mkdir", not from browser.
I can see this folder from my Windows machines (having set samba password), but cannot send files from Windows to it - permission denied. I managed to do this before but have forgotten among all this mess what I did!

---

### Post by kuja on 2008-03-12
Try running sudo chown -R kev:kev /filestore to change the owner from root.

I've had issues with samba since ...... 6.10 I think, maybe it was 7.04. Once I couldn't get it to work I just switched to sftp (seeing as all of my computers are running Linux anyway .. I was just using samba because I'd heard of it first)

---

### Post by KMJones1 on 2008-03-12
I THINK I'VE DONE IT!!
I fiddled with chmod and chown as suggested, and managed to set permissions, and eventually I can copy and access and save files within Ubuntu and from Windows.
If any further problems arise I'll start a new thread.
VERY MANY THANKS TO YOU ALL (esp kuja and prefader)!!
:)

---

