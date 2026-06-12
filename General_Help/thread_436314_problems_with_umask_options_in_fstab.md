---
title: "problems with umask options in fstab"
date: 2007-05-07
forum: General Help
---

### Post by Niall Flinn on 2007-05-07
Hi folks,

I've just bought a nice big USB disk and I'm having some trouble mounting it with the correct permissions. It's formatted with ext3 using gparted, but I don't seem to have any write permissions. I've done some reading on the forums and according to this page:

[https://help.ubuntu.com/community/VolumePermissions](https://help.ubuntu.com/community/VolumePermissions)

...it seems that I need to set the umask options in my fstab, so I've tried the following:

```

/dev/sdb1 	/media/usbdisk 	      ext3   auto,rw,umask=0222	  0       0
```

When I try to mount it with these options, I get the following:

```
wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

If I run dmesg | tail , I get the following:
```

EXT3-fs: Unrecognized mount option "umask=0222" or missing value
```

Any idea what's going wrong?

Cheers,

Niall

---

### Post by Niall Flinn on 2007-05-07
OK, looks like the following fstab was actually all I needed:
```

/dev/sdb1 	/media/usbdisk 	      ext3   auto,rw	  	  0      
```

My actual problem was that I didn't have the correct permissions set on my mount point...

Niall

---

### Post by taurus on 2007-05-07
Personally, I would have an entry like this in /etc/fstab for that USB harddrive.

```
/dev/sdb1 	/media/usbdisk 	      ext3      defaults     0       0
```
Then, I just change the ownership of /media/usbdisk from root to my login name, _assuming_ it's **niall**.

```
sudo chown -R **niall**:**niall** /media/usbdisk
```

---

