---
title: "Two external drives suddenly not mounting properly"
date: 2020-08-14
forum: General Help
---

### Post by germanicus1982 on 2020-08-14
I'm running ubuntu server 18.04.2 with kernel version 5.7.9. Up until today everything was working as it should however, for some reason now I'm getting a really odd problem.

I have two external drives a 4tb mounted at /Media and a 2tb mounted at /Staging. For some reason though now /Media doesn't show as mounted however it's contents are displayed in both /Media and /Staging. /Staging on the other hand shows as properly mounted but it's contents don't show up anywhere. I'm really not sure how to go about troubleshooting this one. Any help would be appreciated.

Thanks.

---

### Post by TheFu on 2020-08-15
Run **mount** to see the actual mount commands, options, locations.  Sadly, the output is ugly.  Also, /Media/ and /media/ are very different.  Usually, storage that a file manager mounts goes to /media/.

If you want control over mount locations and options, then settings have to be placed into /etc/fstab or autofs must be used historically. The last year or so, the systemd team has added storage "unit" files to control mounts, but they don't recommend it last time I looked. There aren't any other methods. If you didn't do those, I don't know how the storage mount locations would be controlled.

The systemd team has been screwing with the fstab for a few years now, certainly trying to make it "better".  For any non permanent storage - either internal or connected with screwed in cables, I'd use the fstab.  For any storage that can accidentally vibrate free of the connection (cough - USB) or all networked storage, I use autofs.  Actually, I do exactly that.  There isn't any GUI tool for these things that I trust to do the right things.

---

### Post by germanicus1982 on 2020-08-15
I used /Media (capital M) on purpose, it's not automounting, I set these mounts up myself. The server is headless too, no window manager.

Here's my fstab for reference.

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sdc2 during installation
UUID=19b5b845-d8b1-4d9f-ad65-f3e29a78fa6e /               ext4    errors=remount-ro 0       1
# /Media was on /dev/sdb1 during installation
UUID=18a0eb0d-7ef2-437d-8f90-40a38aa352df /Media          ext4    defaults        0       2
# /boot was on /dev/sdc1 during installation
UUID=aa33fe39-744d-4eff-b9fd-5188c4794489 /boot           ext4    defaults        0       2
# /home was on /dev/sdc5 during installation
UUID=2379a78a-ff36-472a-b557-2152683ee844 /home           ext4    defaults        0       2
# /windows was on /dev/sdb2 during installation
#UUID=6F8D050E0AAF2187 /windows        ntfs    defaults,umask=007,gid=46 0       0
/swapfile                                 none            swap    sw              0       0
/dev/sdc1       /Staging        ext4    defaults        0       0

```

---

### Post by germanicus1982 on 2020-08-15
If you notice, from the attached picture, for some reason /Staging shows up twice and the second one has the same ID as /Media.

---

### Post by TheFu on 2020-08-15
Did you run the **mount** command - no options?
/dev/sdc can change from boot to boot.  That's why the system uses UUID instead.
**blkid** command will show the UUID to current device mapping.

Sorry, picture don't work for me.  Text only.

---

### Post by TheFu on 2020-08-15
Simplified to see the logical order:

```

UUID=19b5b845-d8b1-4d9f-ad65-f3e29a78fa6e /        ext4 errors=remount-ro 0 1     
UUID=aa33fe39-744d-4eff-b9fd-5188c4794489 /boot    ext4 errors=remount-ro 0 1
/swapfile                                 none     swap sw                0 0     

UUID=2379a78a-ff36-472a-b557-2152683ee844 /home    ext4 defaults          0 2     
UUID=18a0eb0d-7ef2-437d-8f90-40a38aa352df /Media   ext4 defaults          0 2     
**[COLOR="#FF0000"]/dev/sdc1[/COLOR]**                                 /Staging ext4 defaults          0 2

```

Which if those doesn't look like the others?  I changed some options and the last number as the fstab manpage suggests.

BTW, /Staging and /Media need to exist on the / file system. Empty directories. In theory, systemd-mount will mkdir as needed, but I've never trusted new-fangled stuff like that.  If any of these are SSDs, you might want to reduce wear by using the _noatime_ option.  For external devices, may also want to add the _nofail_ option, so boot continues even when that device isn't available.

I'm not a fan of swapfiles. 'nuff said.

---

### Post by germanicus1982 on 2020-08-16
I ended up finding the proper UUID for /Staging, changed that in fstab and it works now.

---

### Post by TheFu on 2020-08-16
> **germanicus1982 said:**
> I ended up finding the proper UUID for /Staging, changed that in fstab and it works now.

Yep, device names can change with every boot. The UUID ensures that the correct partition/file system gets mounted regardless of what the device name is.

---

