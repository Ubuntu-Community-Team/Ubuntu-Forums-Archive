---
title: "Formatted usb flash drive with ext4 but can't write to it."
date: 2016-10-25
forum: General Help
---

### Post by William_Labbett on 2016-10-25
Hi. :confused:

I used gparted to format a 8GB USB stick with ext4 formatting.

I subsequently tried copying a file onto it from the Desktop but I was unable to.

I've no idea how to sort it out so that I can. Any help?

---

### Post by The Cog on 2016-10-25
EXT4 uses standard *nix permissions, and I think a newly formatted drive is only writeable by root. My guess is you need to change the ownership or permissions of the folder after it's mounted. Either make it writable by everyone or make yourself the owner.

---

### Post by William_Labbett on 2016-10-25
PROGRESS :

I came to the possibly erroneous conclusion that what I aught to do is copy the file with su to the drive. I first tried

copying it to /dev/sdc1 (the mount point)

This didn't work so I tried 

[COLOR=#40e0d0][/COLOR][COLOR=#ee82ee][/COLOR]william@william-GA-78LMT-USB3:/$ ls
bin    dev   initrd.img      lib64       mnt   root  snap  tmp  vmlinuz
boot   etc   initrd.img.old  lost+found  opt   run   srv   usr  vmlinuz.old
cdrom  home  lib             media       proc  sbin  sys   var
william@william-GA-78LMT-USB3:/$ cd media/william
william@william-GA-78LMT-USB3:/media/william$ ls
2fbcf78f-1d2d-4607-8cbd-844f61540821  500GB
william@william-GA-78LMT-USB3:/media/william$ ^C
william@william-GA-78LMT-USB3:/media/william$ cd /
william@william-GA-78LMT-USB3:/$ cd home/william/Desktop
william@william-GA-78LMT-USB3:~/Desktop$ sudo cp NewDatabase.kdbx /media/william/2fbcf78f-1d2d-4607-8cbd-844f61540821
[sudo] password for william: 
cp: cannot stat '/media/william/2fbcf78f-1d2d-4607-8cbd-844f61540821/NewDatabase.kdbx': Structure needs cleaning


Still I'm totally stuck.

---

### Post by oldfred on 2016-10-25
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

I try to label partitions so the auto mount uses my label, not some long UUID that I cannot type in.
You can label with gparte, Disks, or manually. Newer gpt partitioning has two labels, one filesystem and one gpt/GUID.

You must make sure not mounted, or use the auto mount /media/$USER/longUUID instead of /mnt/data.


 #if not known to list partitions, change sda5 to your data partition or create multiples with different mount points
# is comment, do not type
sudo parted -l
sudo mkdir /mnt/data
sudo mount /dev/sda5 /mnt/data
#where sda5 needs to be your drive, partition
sudo chmod -R a+rwX,o-w /mnt/data
# Note that the -R is recursion and everything is changed, do NOT run on any system partitions.
#All directories will be 775.
#All files will be 664 except those that were set as executable to begin with.
sudo chown -R $USER:$USER /mnt/data

---

### Post by nothingspecial on 2016-10-25
If you sudo it then it is still owned by root. What you need to do is own it yourself, as described earlier.

---

### Post by Bashing-om on 2016-10-25
William_Labbettl Hello;

In addition to the ups, let me see if I can muddy the waters a bit more .

Let's back up and visit the basics of a linux fille system,

You have a external USB device that you want to access, so one has to "attach" the file system that is on the USB to the operating system that is presently in use.
A couple of ways one can  do this.
As it is the CLI you are interested in, we do this from the terminal .
1st is the need to know what the system identifies the USB device as:
```

sudo fdisk -lu

```
for the legacy MBR file system ..
IF this is the newer EFI system look at the identification from:
```

sudo parted -l

```

Next, one makes a point ( mount point ) to attach to:
```

sudo mkdir /mnt/USB1

```
this mount point can be to any directory that you choose .. /mnt is one of the conventional places is all. And the name "USB1" can be what ever you want it to be as an aid to you what you are accessing . Linux is case sensitive, in that USB does not equal usb.
So now you have the point of attachment,;
Now "mount" it :
```

sudo mount /dev/sdb1 /mnt/USB1

```
where "sdb1" is what may have been the identifier from step 1 .

Now we want to change who owns the files - bear in mind that in linux everything is represented as a file ..., everything ! -- on the USB drive - IF and only IF you are the sole user of the USB device then set the owndershop access rights to "YOU".
```

sudo chown -R william:william /mnt/USB1

```
Now you as "william" have access to the USB drive's file system ( as it is a linux file system and access defaults are set by the system) .

So now at last you can list the contents or what ever you may want to do with this attached file system.

See now:
```

ls -al /mnt/USB1

```
USB1 is your puppy !

Now a warning warning warning .. WHATEVER you mount .. it is your resposability and obligation to UNmount when you are done. Failure to UNmount will result in file system corruption at some level . I leave it to you as an exercise to learn what caches and flushing out to devices are .
UN mount :
```

sudo umount /dev/sdb1

```

Feel free to ask for clarification on anything that you do not understand . We are here to help .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Impavidus on 2016-10-26
> **William_Labbett said:**
> 
I came to the possibly erroneous conclusion that what I aught to do is copy the file with su to the drive. I first tried

copying it to /dev/sdc1 (the mount point)

This didn't work so I tried 
(...)
william@william-GA-78LMT-USB3:~/Desktop$ sudo cp NewDatabase.kdbx /media/william/2fbcf78f-1d2d-4607-8cbd-844f61540821
[sudo] password for william: 
cp: cannot stat '/media/william/2fbcf78f-1d2d-4607-8cbd-844f61540821/NewDatabase.kdbx': Structure needs cleaning

/dev/sdc1 is not the mount point. It's the raw partition on your usb drive. /media/william/2fbc... is the mountpoint. Copying a file directly to /dev/sdc1 instead of to its mount point will mess up the file system on the usb drive, which explains why the later attempts failed too. Normally the second attempt should have worked. If there's nothing of value on that usb drive, better format it to create a fresh file system.

---

