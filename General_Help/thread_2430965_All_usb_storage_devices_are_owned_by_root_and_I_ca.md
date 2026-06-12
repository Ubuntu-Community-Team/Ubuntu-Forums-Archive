---
title: "All usb storage devices are owned by root and I cannot write to them."
date: 2019-11-09
forum: General Help
---

### Post by iconoclast12 on 2019-11-09
I have Lubuntu 19.04 installed to the onboard storage of an Atomic Pi, which is only 16gb.. This is a fresh install without anything modified or edited.. I have a 32gb micro sd card that I formatted, on this system as fat32, that I want to use as my main storage. I have the sd card mounted and showing up with the correct size in the file manager. However, the folders that it's mounted to (in the mnt folder) are owned by root and not me (matt).. All the folders in my home directory are owned by me, and I can write to them and change permissions.. I cannot write to my usb drives/sd cards nor can I change permissions on the folders they're mounted to.. I've also tried changing the folder permissions with the chown and chmod commands like this.. And I do not have permission to change them. I get a "operation not permitted, permission denied" error every time..

sudo chown -R matt:matt /mnt/(device name)
sudo chown -R matt:matt /media/usb0 (or usb1)

If I unmount the drives, and try to change ownership permissions on one of these folders, it works and it becomes owned by user matt and group Matt until they drive becomes mounted again (where it shows up in the file manager GUI) and then they become owned by root again.. I've also made myself part of the root group as well.. So I don't really know what's going on here.. I've attached pictures to view so hopefully that helps.

[IMG]https://mail.google.com/mail/u/0/?ogbl#inbox/QgrcJHsHnPgtqtqJpmMKWKSgKNFgrzCGSsV?projector=1[/IMG]

---

### Post by CatKiller on 2019-11-09
> **iconoclast12 said:**
>  I have a 32gb micro sd card that I formatted, on this system as fat32

FAT doesn't understand permissions. You set who can write to a FAT partition with its mount options.

---

### Post by iconoclast12 on 2019-11-09
I formatted it as FAT, because I need to access it over a network share from a Windows PC.. So, I wanted to use this sd card as main storage, and setup a network share with it.. What file system does it need to be formatted for in order to write to it then?

---

### Post by iconoclast12 on 2019-11-09
If I format it as Ext4 will I be able to access it from a Windows computer over a network share if I set it up in Samba?

---

### Post by CatKiller on 2019-11-09
The partition's filesystem is entirely irrelevant to a network share. The remote computer isn't writing directly to the device.

You can read and write to Windows' filesystems from Ubuntu if you use the correct mount options. There are approximately a bajillion articles about mounting Windows filesystems in Linux that will describe those options, as well as the manpage for the mount command. 

Formatting it as ext or f2fs will mean that you can't read the card itself if you were to stick it in a Windows computer.

---

### Post by TheFu on 2019-11-09
> **iconoclast12 said:**
> I formatted it as FAT, because I need to access it over a network share from a Windows PC.. So, I wanted to use this sd card as main storage, and setup a network share with it.. What file system does it need to be formatted for in order to write to it then?

If you plan to use Samba for access from Windows, then any native Linux file system which supports **chown** and **chmod** (all standard Unix permissions) should be used.  I'm not up on flash memory longevity except to know that there are flash specific Linux file systems which can do this.  F2FS comes to mine. There are a few others. I don't know any that are widely used.

ext2 is not a journalled file system, so it would be kinder on the flash storage than ext3/4.  If you go with ext2, then get name-brand SDHC storage with ultra-lifespan properties, i.e. not the cheap stuff. I've burned through a USB3 Sandisk storage device in just over a year before it refused to store any more data, ever. A few weeks later, it refused to allow read of any data too.

On SSD and spinning disks, please use ext4 or ZFS or XFS. I say that just for clarity.

Samba is happier with native Linux file systems. There are some sharing configurations where fine control over different groups and users are important to Samba.  The smb.conf file manpage has all the samba options.

Lacking any more data, if I had to setup what you've described, I'd use a quality flash storage device with ext2.
If you have any plans to plug this storage directly into any Windows machine to have access, that is NOT supported by my solution. Only network-based access using any of the many, many, network methods could be used. Samba, NFS, sftp, scp, rsync, .... or 50 others.

---

