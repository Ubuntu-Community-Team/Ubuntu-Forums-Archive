---
title: "persistent file on hdd"
date: 2013-02-16
forum: General Help
---

### Post by mick222 on 2013-02-16
is it possible to run ubuntu from a usb stick but store changes on a windows hard drive. I am using a family members  computer and don't want to dual boot.I only have a 4gb stick available which limits the size of file to 1gb on the usb.

---

### Post by Ms. Daisy on 2013-02-16
> **mick222 said:**
> is it possible to run ubuntu from a usb stick but store changes on a windows hard drive. I am using a family members  computer and don't want to dual boot.I only have a 4gb stick available which limits the size of file to 1gb on the usb.
I suppose you could mount the Windows hard drive and save files to it.  However unless you save them in a format that Windows will recognize, they will be unreadable inside of Windows.  You can then make the Windows hard drive automatically mount.

See ```
man mount
```and [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by mick222 on 2013-02-16
thx sorry i know how to mount a drive but was hoping to be able to save my home to wundows or a small partition on the windows drive. I now think that was a bit stupid.

---

### Post by sudodus on 2013-02-16
> **mick222 said:**
> 
is it possible to run ubuntu from a usb stick but store changes on a windows hard drive. I am using a family members computer and don't want to dual boot.I only have a 4gb stick available which limits the size of file to 1gb on the usb.

thx sorry i know how to mount a drive but was hoping to be able to save my home to wundows or a small partition on the windows drive. I now think that was a bit stupid.

No question is stupid. And this one can probably be answered with yes. Some linux systems, for example ***Knoppix***, are made to save files and settings like that. It might be more difficult to do with Ubuntu, because its persistent live system is designed to use a file or partition on the USB drive with the name ***casper-rw*** if such a file or partition exists. I have not tried if Ubuntu can use such a file on another drive, but it is worth trying.

But you are actually too pessimistic about your 4 GB USB drive.

1. Make one partition of the whole drive and format it to FAT32, and make it the boot partition.

- Use ***unetbootin*** to make it a persistent live drive with Lubuntu or Xubuntu, and ask it to create a file of 4GB for persistence. Then it will install the operating system and use all remaining space for persistence, approx. 3GB.

2. Or make one partition of 1GB and format it to FAT32. Make another one of the rest of the drive and format it to ext4. Add the label casper-rw. Then make it a persistent live drive with ***usb-creator-gtk***

---

### Post by schragge on 2013-02-16
I guess you also can mount the Windows hard drive, create a file there, then prepare, format, and mount it as loop device under another mount point in Ubuntu. See an example at the end of [losetup(8)]("http://manpages.ubuntu.com/manpages/precise/man8/losetup.8.html") manual page.

---

### Post by mick222 on 2013-02-16
thx all remember puppy could do this and thought it might be possible in ubuntu.Tried that   sudodus but want some large files on it  might have had more luck with lubuntu ,decided to ask for a small partition to install ubuntu on. just want to test drive raring on a computer. thx all thread closed.

---

### Post by C.S.Cameron on 2013-02-16
You can create an ext4 partition on the hard drive and label it "casper-rw".
When booting a persistent flash drive it will use this partition for saving stuff.
The casper-rw file may or not be removed from the persistent flash drive, however the HDD partition will have priority.

---

### Post by sudodus on 2013-02-16
> **C.S.Cameron said:**
> You can create an ext4 partition on the hard drive and label it "casper-rw".
When booting a persistent flash drive it will use this partition for saving stuff.
The casper-rw file may or not be removed from the persistent flash drive, however the HDD partition will have priority.
I'm reading and learning :-)

It is good to know that a casper-rw partition on the internal drive will have higher priority than a casper-rw file on the USB boot drive.

Do you know the complete priority ranking?

Internal casper-rw partition
Internal casper-rw file
External casper-rw partition (on the USB boot drive)
External casper-rw file (on the USB boot drive)

Is the priority in alphabetical order of the drives or something else? Is there a link describing this?

---

### Post by C.S.Cameron on 2013-02-17
> **sudodus said:**
> I'm reading and learning :-)

It is good to know that a casper-rw partition on the internal drive will have higher priority than a casper-rw file on the USB boot drive.

Do you know the complete priority ranking?

Internal casper-rw partition
Internal casper-rw file
External casper-rw partition (on the USB boot drive)
External casper-rw file (on the USB boot drive)

Is the priority in alphabetical order of the drives or something else? Is there a link describing this?

I'm not totally sure, I think highest priority goes to casper-rw partition on drive with highest priority in BIOS and then to casper-rw file closest to root of the persistent drive.

I only noticed the above when trying to boot my EEE, with persistent HDD install, using a persistent flash drive., I got quite confused for a while.

---

### Post by sudodus on 2013-02-17
> **C.S.Cameron said:**
> I'm not totally sure, I think highest priority goes to casper-rw partition on drive with highest priority in BIOS and then to casper-rw file closest to root of the persistent drive.

I only noticed the above when trying to boot my EEE, with persistent HDD install, using a persistent flash drive., I got quite confused for a while.
Thank you

---

