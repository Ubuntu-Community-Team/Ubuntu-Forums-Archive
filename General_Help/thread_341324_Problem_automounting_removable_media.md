---
title: "Problem automounting removable media"
date: 2007-01-18
forum: General Help
---

### Post by ofjord on 2007-01-18
Hi, I have a few computers running ubuntu using a debian server with an LDAP directory for authentication for a few users. All the users belong to the same LDAP group.

The problem is, a regular user cannot automount usb sticks and usb removeable hard drives.

They show up in 'Computer' but when i right-click and do 'Mount Volume' I get the following error:

error: could not execute pmount

Anyone have a clue?

---

### Post by bswilson on 2007-01-18
The `mount` command can only be used by root or a superuser.  That is why `pmount` exists; its job is to mount removeable devices with the normal user's permission.  Essentially, for a normal user `pmount` does the job of automounting a device.

You should read the man pages for `pmount`; specifically the POLICY section that describes the conditions that must be met for a user to be able to invoke `pmount`:

```
POLICY
       The mount will succeed if all of the following conditions are met:

       · device is a block device in /dev/

       · device is not in /etc/fstab (if it is, pmount executes  mount  device
         as the calling user to handle this transparently)

       · device is not already mounted according to /etc/mtab and /proc/mounts

       · if the mount point already exists, there is no device already mounted
         at it and the directory is empty

       · device   is   removable   (USB,   FireWire,   or   MMC   device,   or
         /sys/block/drive/removable is 1) or whitelisted in /etc/pmount.allow.

       · device is not locked
```

---

### Post by ofjord on 2007-01-18
I believe all these conditions are met. I think this is simply a permission problem.

I have tried changing the group in /etc/udev/rules.d/40-permissions.rules to the group users belong to but it didn't work.

I have also tried whitelisting the device in /etc/pmount.allow with no luck.

Device is not in fstab and not already mounted



Any other methods for assigning a group permission to automount?

---

### Post by dcstar on 2007-02-03
> **ofjord said:**
> Hi, I have a few computers running ubuntu using a debian server with an LDAP directory for authentication for a few users. All the users belong to the same LDAP group.

The problem is, a regular user cannot automount usb sticks and usb removeable hard drives.

They show up in 'Computer' but when i right-click and do 'Mount Volume' I get the following error:

error: could not execute pmount

Anyone have a clue?

AFAIK the users must be in the pmount group to have permission to mount.

---

### Post by loney on 2007-05-17
user must be in plugdev group rather than pmount group.


/usr/bin/pmount must also be executable. I had to change permissions as follows:

 sudo chmod a+x /usr/bin/p*mount

I don't know why execute permission is not set on these files by default. Is this an install bug?

---

