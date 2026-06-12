---
title: "What to do when dd destroys your usb-stick?"
date: 2016-10-29
forum: General Help
---

### Post by kiina on 2016-10-29
How to recover your USB-stick when it's been destroyed by dd? 
Sometimes *dd if=/source of=/destination* change your USB-stick size and it's unusable then.

---

### Post by yetimon_64 on 2016-10-29
Can you give us the exact command you used please ? Doing so will tell us exactly how and to what degree that command has affected the usb stick. In the terminal use the up and down arrows on the keyboard to go through the terminal history to find the command if you don't remember it off hand and copy/paste it back here for checking.

If you have deleted the complete device including the partition table of the usb stick you may need to install gparted and add a new partition table before you can add or format any new file systems on the usb stick. It will depend on the command you used originally though.

You may possibly be able to reformat the usb stick using gparted and add a new partition table and filesystems, but depending on the command you used it is highly likely any old data on the usb stick will be totally unrecoverable. dd is often nicknamed "data destroyer" for a good reason and can be a potentially dangerous/catastrophic command to "play" or experiment with for an inexperienced user. Always use it with extreme care.

---

### Post by Dennis N on 2016-10-29
After writing to it with dd, to return to normal use for storing files create a new partition table and then create an FAT32 partition. Then it should work again.

Use gparted, and select the USB in the drive selector (upper right):
Device > Create Partition Table > MS-Dos

After this completes, select unallocated space, then
Partition > New
Set desired size of partition (usually the maximum), and select to format FAT32

---

### Post by Bucky Ball on 2016-10-29
The nickname of dd is 'disk destroyer' (or, I notice from yetimon_64, 'data destroyer', though I've never heard that one), for appropriate reasons. It will obliterate whatever you've pointed it at which is why you need to double, triple, quadruple check the target before hitting the button.

Problem is, dd obliterates the data *before* it writes the new data on there. I don't like your chances of recovering what was there before, but good luck. Probably better to user something safer next time.

---

### Post by yetimon_64 on 2016-10-29
> **Bucky Ball said:**
> The nickname of dd is 'disk destroyer' (or, I notice from yetimon_64, 'data destroyer', though I've never heard that one)...

Mine is a combination of its normal name "data dump" and its other nickname "disk destroyer" after I overwrote and lost 75 GB of data on one of my data partitions few years back :(. I have heard it called many names over the years, quite a few "unprintable" ones as well when used carelessly here ;).

> **Bucky Ball said:**
> ...Probably better to user something safer next time.
+1, there are safer alternatives when copying data. dd is a very low level disk access tool, hence dangerous if not used absolutely correctly.

@OP, it would be nice to see the exact command if possible. Though if you are seeing a reduction in disk size and are unable to use it, it really doesn't sound like you will get much back off such a stick.

---

### Post by HermanAB on 2016-10-29
OK, to answer the original question:
Sometimes the only way to recover a USB memory thingy is to zero the first megabyte (more or less) and then format it with gparted.  Zeroeing it will ensure that gparted (or even a Windows machine) will think that it is a new device and will then format it properly.

First check the device name:
Unplug it
# dmesg
To get some idea of what it looks like when not plugged in

Now plug it in
# dmesg
and you should see the device name, eg /dev/sdb

You can zero a device with something like this:
# dd if=/dev/zero of=/dev/sdb bs=1M count=1

Now you can run gparted to format it with your favourite file system.

---

### Post by sudodus on 2016-10-29
Or you can use ***mkusb***, that wraps a safety belt around ***dd***. It does similar things under the hood to help you identify the correct target device as *HermanAB* describes,

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

If you run standard Ubuntu, you need an extra instruction to get the repository Universe. (Kubuntu, Lubuntu ... Xubuntu have the repository Universe activated automatically.)

```
sudo add-apt-repository universe  # only for standard Ubuntu

sudo add-apt-repository ppa:mkusb/ppa  # and press Enter
sudo apt-get update
sudo apt-get install mkusb mkusb-nox usb-pack-efi
```

and specifically to restore the drive, use the first option in the wipe menu: [mkusb/wipe](https://help.ubuntu.com/community/mkusb/wipe)

**s "Standard: create MSDOS partition table with FAT32 partition" **

-o-

***Edit:*** But if your problem is that you want to recover files, that were there before you made it into a USB boot drive, you have tough luck. The first part of the drive, maybe 1.3 GB is completely overwritten by the cloned copy. If files were stored 'behind' that part of the drive, they might be possible to recover with ***PhotoRec***. See this link: [cgsecurity.org](cgsecurity.org)

---

