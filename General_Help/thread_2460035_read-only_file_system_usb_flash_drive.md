---
title: "read-only file system usb flash drive"
date: 2021-03-31
forum: General Help
---

### Post by tendouser on 2021-03-31
how may i switch to read/write a usb stick?

---

### Post by guiverc on 2021-04-01
It is an actual install or an ISO written to the thumb-drive?  

If it's a *live* installer on the thumb-drive, the image/ISO is written as a read-only medium (persistence is on another portion of the thumb-drive; ie. part is RO & part is RW). 

But you've given no real specifics as to why it's RO; was it mounted that way? what type of file-system is it?  maybe it flips from RW to RO because of errors? so did you explore messages on the `mount`?

---

### Post by HermanAB on 2021-04-01
It may be time to backup your backups...

---

### Post by ActionParsnip on 2021-04-01
What file system are you using? Details please! You can't just "make a USB stick writable". Its a file system. A very complex creature with ACLs and so on.....we aren't psychic. Can you give any detail about the stick like the file system you are using? size? If the stick has ever been writable? If you use the safe remove feature before physically removing the device?

---

### Post by tendouser on 2021-04-01
it's a live linux usb created with cp command
and iso file

i have tried remount,rw with no success

---

### Post by ActionParsnip on 2021-04-01
You don't create a bootable usb stick with cp. You need to use a tool like unetbootin or Rufus. Simply copying the ISO to the USB as a file isn't sufficient to make an installation media. Is this what you are trying to do?

---

### Post by TheFu on 2021-04-01
> **ActionParsnip said:**
> You don't create a bootable usb stick with cp. You need to use a tool like unetbootin or Rufus. Simply copying the ISO to the USB as a file isn't sufficient to make an installation media. Is this what you are trying to do?

cp CAN definitely be used to create a bootable Try Ubuntu flash drive, provided the target is a whole drive and correctly specified:
```
sudo cp /path/to/ubuntu-xxxxxxx.iso /dev/sdz
```
Other commands that copy bits unmolested from A --> B can be used too.  dd, ddrescue, cat, cp all can be used.  I have never used unetbootin or Rufus - ever.  The example above with "sdz" is incorrect. The actual device needed will depend on which device has the connected USB storage in each computer. While possible, in theory to be sdz, that is highly unlikely. I'd use **dmesg -w** to watch as the USB device is connected to see the correct whole drive device.  Don't specify a partition.

However, an ISO file system is read-only and cannot be changed after the fact.  It is always read-only, just like a DVD or CDROM is read-only. That's a limitation of the ISO9660 file system.

There are 2 alternatives if a read-write setup is desired on flash storage.  Flash storage will be abused with either, since every storage cell has a limited number of writes allowed, but most people can get a year from something like this before the flash cells are all out of write cycles and the stick dies.

Option A) Install Ubuntu using the normal installation method onto another USB stick.  This will be just like installing to an external USB spinning disk or SSD, but flash memory doesn't allow anywhere near the same number of write-cycles.

Option B) Use a tool like **mkusb** to create the installation AND setup some ext4 data storage at the same time.  mkusb is a tool that copies over the ISO file, which will remain read-only, but also allows an ext4 partition to be used in an "overlay" way so the OS appears to be read-write. At least every quarter, though weekly would be more secure, you'll want to rebuild the ISO part to get kernel updates.  There is a huge thread in these forums about mkusb.  I've only played with it a few times last summer. Some of the options were confusing to me because they didn't use sufficient technical terms for my clear understanding, but on the 2nd attempt, I finally understood what choices created the results I desired.  

I found it easier to just do an install onto a portable SSD for my needs, but I had a spare m.2 SATA SSD and a $9 USB3 m.2 external enclosure already.  Also, my computers aren't nasty towards booting from USB storage, like some computers are.

---

### Post by ActionParsnip on 2021-04-01
Learning every day

---

### Post by TheFu on 2021-04-01
> **ActionParsnip said:**
> Learning every day

Me too.  Hammonds taught me that.  ;)
There's always more to know which is good and bad.

---

### Post by C.S.Cameron on 2021-04-02
The method shown here [https://askubuntu.com/a/1176695/43926](https://askubuntu.com/a/1176695/43926) mentions UNetbootin but should work for adding persistence to an extracted system as I understand you have.

---

