---
title: "How do I mount an external drive so it's Read/Write?"
date: 2007-04-01
forum: General Help
---

### Post by Peet42 on 2007-04-01
Hi.  Can someone help, please...

I'm running the 6.06 x64 Live CD, which sees and mounts my external USB (ext3) drive, but only mounts it read-only.  I've played around in the Terminal with *'sudo chmod'*, but I can't set the ownership to "ubuntu" to let me change the permissions.

Can someone talk me through it, please?  It's device *sdb*, and the partition I'm trying to write to is */dev/sdb1* on */media/usbdisk*.

Basically, I need to copy files off a broken system before I reformat.

---

### Post by spin2cool on 2007-04-01
try this:
```

sudo umount /media/usbdisk
sudo mount -t ext3 -w /dev/sdb1 /media/usbdisk

```

---

### Post by spin2cool on 2007-04-01
to clarify, we're unountind the drive first, then remounting it with write premissions enabled (using the -w switch)

---

### Post by Peet42 on 2007-04-01
spin2cool, I tried that before.  It just comes back with an error:

*"Mount: /dev/sdb1 is not a valid block device."*

I'll try again, in case I did something subtly different the first time, but I suspect it'll do the same and I'll need to reboot to make the drive accessible again. :-/

---

### Post by tacm on 2007-04-01
it is amazing to me that I am doing the exact same thing right now........I too got the same error.   All I had to do was unplug the drive and re plug it into the usb port and I could "see" the drive again.  Also the file browser comes up usb drive AND usb drive1 does that mean there is a partition on this drive?????

---

### Post by Peet42 on 2007-04-01
Unfortunately, it would appear that the supplied version of *"mount"* doesn't recognise the *"-w"* switch.  Any other ideas...?

---

### Post by Peet42 on 2007-04-01
tacm, was your drive originally attached to a "Slug" or other network device?  If so there's a 20MB partition with all the filesystem stuff for that, which you don't see normally.

---

### Post by tacm on 2007-04-01
im not really sure......it was a drive my father loaned me to back up my system on so I can send my lap top off  for warranty work

---

### Post by Peet42 on 2007-04-01
If it was a Windows drive, it just means there were two partitions there.  Each one gets assigned to a different logical drive.

---

### Post by spin2cool on 2007-04-01
try adding the drive to your fstab.  Add a new line with something like:

```

/dev/sdb1 /media/whatever ext3 defaults 0 2

```

Then, remount everything in fstab with 
```

sudo mount -a

```

---

### Post by spin2cool on 2007-04-01
I should have specified that the file in question is "/etc/fstab"

```
sudo gedit /etc/fstab
```

---

### Post by Peet42 on 2007-04-02
I just get *"/dev/sdb1 is not a valid block device."*

I'm beginning to suspect there's a problem with the filesystem on the external drive that's leading to it always being mounted read-only. :(

---

### Post by Kristopher on 2007-04-02
Was just looking to do this with my Vista partition under Ubuntu 7.04, I found this

[http://onlyubuntu.blogspot.com/search/label/ntfs-config-ubuntu](http://onlyubuntu.blogspot.com/search/label/ntfs-config-ubuntu)

Let me know if it helps you.

---

### Post by Peet42 on 2007-04-02
I'm afraid that doesn't help.  It's specifically about mounting Windows drives under NTFS, and I need to mount a Linux drive under EXT3. :'(

---

### Post by Kristopher on 2007-04-03
Does this help [http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by Kristopher on 2007-04-03
Or you could install it as a VM

---

### Post by fanatik on 2007-04-03
Hmm my dad had a similar issue with a USB SD card reader.... it took me ages to work it out, and to be honest I am still unsure what it was (maybe a faulty reader device), but the way to work around it was to boot with it connected, rather than plug it in after booting. That was in OpenSuse, which it seems you are using too... So try that and see if it's mounted r/w.

If not, paste in the contents of:

dmesg | grep sda

Cheers,
James.

---

