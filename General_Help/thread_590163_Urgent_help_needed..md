---
title: "Urgent help needed."
date: 2007-10-24
forum: General Help
---

### Post by billgoldberg on 2007-10-24
I'm typing this on my ubuntu laptop. I can't use my big pc.

On the big pc, I had a harddrive with two partitions.

The first one had ubuntu feisty, the second had vista home premium.

My brother only wants windows, he needed more space for media and since it is his computer I formatted the  ubuntu partition using some windows partition tool.

I new grub would give an error, so I pulled out the super grub disk cd to repair vista mbr.

THats where i'm stuck.

For some reason, no cd i put into the cd drive will boot. I tried several cd's that booted on other pc's (gparted live cd, super grub disk, windows vista, windows xp, ubuntu 7.04 live cd, linux mint live cd, pclinuxos 2007, ...)

The bios is set to boot from cd first, and the bios recognises the cd drive.

I tried installing super grub disk and gparted on my 1gb creative zen stone, but they instructions are to complicated.

Can anyone give simple instructions to install those on usb flash disk or another solution
(besides installing new cd drive)?

Thanks

---

### Post by billgoldberg on 2007-10-24
I really need help guys, i can't use the pc anymore and it's only a month old.
I don't want to pay a $200 or more for this.

---

### Post by -Zeus- on 2007-10-24
Can't you press one of the F keys during startup?  Try F12 and pick the CD

also, waiting for more than 10 minutes for an answer WOULD help...

---

### Post by billgoldberg on 2007-10-24
It's a packard bell, I used all the f keys, none works.

It won't boot any cd's.

---

### Post by -Zeus- on 2007-10-24
and you're sure that the CD is set to first boot in BIOS? and you saved the changes to the BIOS?

---

### Post by billgoldberg on 2007-10-24
yes

---

### Post by logos34 on 2007-10-24
as far as usb goes have you tried this howto:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob)

---

### Post by billgoldberg on 2007-10-24
> **logos34 said:**
> as far as usb goes have you tried this howto:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#bob)

Yes.

The steps there aren't very clear (to me). These are the instructions

> 
Detailed how-to:

herman@red:~$ cp sgd_usb_0.9577.tar.gz /tmp
Copy your downloaded SuperGrub Disk tar.gz (compressed) file to your /tmp directory.

herman@red:~$ cd /tmp
cd to your /tmp directory.

herman@red:/tmp$ tar xvzf sgd_usb_0.9577.tar.gz 
Untar (decompress) your file.

herman@red:/tmp$ ls -lt
total 222
-rw-r--r-- 1 herman herman 224773 2007-02-07 18:02 sgd_usb_0.9577.tar.gz
drwxr-xr-x 3 herman herman   1024 2007-01-28 03:50 sgd_usb_0.9577
List the files in your /tmp directory to see that the sgd_usb_0.9577 file is there.


herman@red:/tmp$ cd 
cd back home.

herman@red:~$ cp -R /tmp/sgd_usb_0.9577/boot /media/usbdisk
We don't want the whole sgd_usb_0.9577 directory, only the /boot directory which is inside it.
Copy the /boot directory from /tmp/sgd_usb_0.9577 to your USB disk.

herman@red:~$ sudo grub
Open a  GNU GRUB shell with root priveledges.

[ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> geometry (hd
 Possible disks are:  hd0 hd1 hd2
Take a look to see what disks you have by using 'tab completion'. For this trick I have only typed most of the command and not completed it. Then I press 'Tab', and GRUB suggests possible ways for me to finish typing the command.
This tells me that I have three hard disks in this machine. Two will be the hard disks inside the computer, and one will be my external USB disk. I guess (hd2) will probably be the USB disk, but I'll need to check.

grub> geometry (hd2)
drive 0x82: C/H/S = 7936/1/32, The number of sectors = 253952, /dev/sda
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
Okay, I completely typed (hd2) this time, but I want to check to be sure (hd2) is indeed my USB disk and not some other disk inside my computer.
The output here tells me that this is the correct disk because I happen to know that I have a lot of partitions in the other disks but this one only has one partition and it's only a small disk, so this confirms to me that (hd2) is my USB disk. Good.

grub> root (hd2,0)
The 'root' command tells GRUB to focus all its attention in the USB disk's file system. So, in other words, it will be the USB disk's GRUB we will be installing. If we didn't do this, we might be installing our hard disk installed GRUB to the USB disk by mistake. We want to be sure it will be the GRUB from the Super Grub Disk /boot directory that we just copied to the USB disk that gets installed there.

grub> setup (hd2)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd2)"...  24 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd2) (hd2)1+24 p (hd2,0)/boot/grub/stage2 /boot/grub/menu.lst"... succeeded
Done.
It looks like we have done it!
The setup command shown here installs GRUB to MBR in the USB disk.


grub> quit
This command is to quit the GRUB shell.

herman@red:~$ exit
This is just to to exit the terminal.



If I follow the exact codes he gives, i'm stuck at the first line. Always give me an error. I just untar and copy the boot folder to the usb stick (fat32). Then do "root (hd1,0)" and then "setup (hd1)".
This gives me the error: error 17 unable to mount volume (or something like that)

---

### Post by billgoldberg on 2007-10-24
At this point i'm even willing to use windows xp to fix the problem, if something like super grub disk for usb exists for windows, let me know.

---

### Post by logos34 on 2007-10-24
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)

Not sure what the problem is.

Does your 'big' pc have a floppy drive?  Because you could try using Smart Boot Manager floppy to force the computer to boot from cd

---

### Post by adrian15 on 2007-10-25
> **billgoldberg said:**
> If I follow the exact codes he gives, i'm stuck at the first line. Always give me an error. I just untar and copy the boot folder to the usb stick (fat32). Then do "root (hd1,0)" and then "setup (hd1)".
This gives me the error: error 17 unable to mount volume (or something like that)

I do not like Herman instructions myself.

Let's see. You run:
```

mount

```
and you save the result somewhere else.
You then plug in the pendrive. Close the just opened windows.
Run
```

mount

```
and see what's the pendrive device. Something like /dev/sdc or whatever it is ( You will find it in the one more line that it's added to the first mount output).

Now you should run:

```

umount /dev/sdc

```
where /dev/sdc is your pendrive device.

Now let's do:
```

grub
grub>device (hd3) /dev/sdc
grub>root (hd3,0)
grub>setup (hd3)
grub>quit

sync


```

and you are done.

Now reboot as usual and see if the usb can boot or not.

adrian15

---

### Post by billgoldberg on 2007-10-26
Sorry for the late replies. Have been busy.

I follow the instructions you gave, but another error pops up when trying to install super grub disk to usb stick.

To be clear: I downloaded sgd_usb_0.9590, extracted it and copied the boot folder to usb stick.

Then I did : "mount" wich gave me this:
> 
rw@beast:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
fusesmb on /home/rw/Network type fuse (rw,nosuid,nodev,allow_other,max_read=32768)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)


Then I did the same with the usb stick in the machine

> 
 mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
fusesmb on /home/rw/Network type fuse (rw,nosuid,nodev,allow_other,max_read=32768)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077)


Then I did "umount /dev/sdb1"

This gave me this
> 
umount: /dev/sdb1 is not in the fstab (and you are not root)


Then I did "sudo umount /dev/sdb1"

This gave me a new line

> 
rw@beast:~$ sudo umount /dev/sdb1
Password:
rw@beast:~$ 


Then I did i did "grub"

then
grub> device (hd1) /dev/sdb1

Then I did
grub> root (hd1,0)

Error 18: Selected cylinder exceeds maximum supported by BIOS

Then I tried
grub> root (hd1)

That seemed to work, well it didn't give any errors, but then the next step did

grub> setup (hd1)

Error 17: Cannot mount selected partition

So i'm stuck again.

For the record, I tried it on an 256mb and an 1gb usb stick.

---

### Post by adrian15 on 2007-10-29
> **billgoldberg said:**
> 
grub> device (hd1) /dev/sdb1


I am sorry in this step you should write the linux hard disk device not the partition one.

That means writing:
```

grub> device (hd1) /dev/sdb

```

Go ahead and tell us if you can get your own USB SGD right now.

Thank you.

adrian15

---

