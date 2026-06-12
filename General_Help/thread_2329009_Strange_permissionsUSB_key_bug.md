---
title: "Strange permissions/USB key bug"
date: 2016-06-27
forum: General Help
---

### Post by kazakore on 2016-06-27
I have just plugged in my USB to transfer a couple of files to it for printing at an internet cafe. It mounts correctly, I have deleted the files that were on there no problems and I can create new folders and files without issues. However whenever I try and copy a file onto it I get an error message saying the device is Read Only when this clearly isn't the case.

I use Ubuntu Studio but I guess as I have a non-standard installation with Thunar 1.6.3 from Trusty installed in place on 1.6.10 as features which are missing from the latest version are critical to the way I work I guess I will get little help on here. I'm in the process of installing gparted to see if it works after a reformat. Still had anybody come across behaviour like this before?

$ df -t
/dev/sdb1      vfat       7830556         4   7830552   1% /media/dale/Keyring

$ ls -la /media/***/
drwxr-xr-x   2 *** *** 4096 Jun 27 14:16 Keyring

EDIT:
Well that was weird! After formatting with GParted it would only mount with root as owner so I it really was read only from my userspace. It also reverted to a name of an old Live distro I had on there once upon a time (noticed GParted do this a lot in the past, labels from old usage seem to come to the surface.)

Before installing I had done a update/upgrade as it had been a few days.

Restarting the laptop and it froze with the USB inserted, as if it really did think it should have been a bootable USB device (which it was once upon a time.) But removing and restarting and I have mounted and copied files to it successfully.


Can can anybody tell me how to do a full, true format to FAT32 using GParted, or another recommended tool, rather than the quick formatting which leave the data there and I believe may be the source of some of this weirdness?

Well the Windows machine in the internet cafe couldn't even read it. Formatting on Linux really needs to be sorted out! Is there anything more recommended that GParted?

---

### Post by Impavidus on 2016-06-27
In my experience, gparted has no trouble formatting to FAT32.

When a usb drive or any other kind of storage device suddenly turns read-only, it usually indicates there was an I/O error, which is usually caused by a hardware problem. Have you tried a different drive or a different port?

---

### Post by kazakore on 2016-06-27
As I said it wasn't really Read Only. I could delete the files already on there. I could create new file and folders. But I couldn't copy files from another location onto it. And it still doesn't explain the strange behaviour I've very often seen with GParted on bringing back old label names on reformatting a device or the fact the laptop seemed to be trying to treat it as a bootable device.

Maybe I should always recreate the partition table as well as I think this can help sometimes...

---

### Post by sudodus on 2016-06-27
You wrote that this USB drive was once a boot drive. There might be some trace left from that time, maybe in the first megabyte. In the wipe menu of mkusb, you can try different methods to create systems that should make it work. See these links,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

[mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

There might be problems in the internet café because of some flag or missing flag in the partition table of the FAT32 file system (and I guess an MSDOS parttion table). Maybe it will work better as a data drive also in Windows with a GUID partition table (GPT) and an NTFS file system. This is an option in the wipe menu of mkusb.

**b "Big drive: create GUID partition table with NTFS partition" **

-o-

If you have problems with permissions in linux, you can mount it manually and use the cp command with superuser privileges. If you want to use it many times, it is better to change the ownership and/or permissions of the mount point because all directories and files in Microsoft file systems will inherit the permissions of the mountpoint (you might be able to specify it differently with a mount option).

Run once:
```
sudo mkdir /mnt/pt1
sudo chown $USER /mnt/pt1  # make your own user ID owner
sudo chmod 775 /mnt/pt1    # set permissions

```

Check with parted and use the information to mount the drive:
```
sudo parted -ls
sudo moount /dev/sdxy /mnt/pt1
```
where x is the drive letter and y is the partition number, typically b and 1, so typically /dev/sdb1

Copy the files
from the current directory:
```

cp file1 file2 /mnt/pt1       # or
sudo cp file1 file2 /mnt/pt1  # with sudo to get superuser privileges

```

from any directory with absolute path:
```
cp /path1/file1 /path2/file2 /mnt/pt1
```

If you get the ownership and permissions right, you should also be able to see /mnt/pt1 with Thunar and copy graphically (drag and drop).

---

### Post by kazakore on 2016-06-27
Thanks for the useful information. I think there may have been something strange with the PC in the internet cafe, it got further when I tried again after having also recreated the partition table and entered a label for the drive name rather than leave it blank. Still seemed slightly odd with the way it mounted it (the drive appeared to contain a link to itself) and I wasn't sure if the files didn't display due to whatever pdf program they had not working or the files. Had also emailed myself them that time and printed directly from Chrome in the end...

But I didn't know GPT was suitable for small flash storage. I've always avoided ntfs due to old issues with compatibility but I guess they're non-existant there days. If I wanted to make sure something could ne read across Linix,Windows and Mac/OSX I would go with MPT and FAT32. Is GPT and NTFS a better choice these days? I knows things like music players with a USB port still generally need MPT/FAT32 but it's not often I use them at all...

---

### Post by sudodus on 2016-06-28
GPT is a more modern and reliable partition table than the MSDOS partition table.

NTFS is a more modern and reliable file system than FAT32. It works well with Windows and linux. But if you want compatibility with MacOS, you should stay with FAT32.

I think you are right, many small devices like mp3 players work only with an MSDOS partition table and FAT.

There is also exFAT, which can sometimes cause problems. It is a proprietary file system owned by Microsoft. There are tools to manage it in linux. You can often avoid it, but some flash memory cards are designed to use it exclusively(?!) See this link

[https://en.wikipedia.org/wiki/Secure_Digital](https://en.wikipedia.org/wiki/Secure_Digital)

Some people prefer the UDF file system. It is very portable but I think it lacks tools to repair the file system.

[http://tanguy.ortolo.eu/blog/article93/usb-udf](http://tanguy.ortolo.eu/blog/article93/usb-udf)

---

