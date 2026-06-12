---
title: "Change drive label in Quantal"
date: 2012-11-14
forum: General Help
---

### Post by stinkeye on 2012-11-14
How do you change the drive label for a usb storage device.
eg my sansa clip mp3 player.
Did this in previous releases in disk utility.

Using gparted, I can change the label on a Fat formatted usb stick, by unmounting first.
But the mp3 player drive shows up as unallocated in gparted.
I can browse the mp3 player files in nautilus though.

---

### Post by gerowen on 2012-11-14
The "Disk Utility" has been updated to fit in with Gnome3/Unity and is now just called "Disks".  Just open it, highlight the partition you want to modify, click the little gear icon under it, and click "Edit Filesystem Label".  A screenshot is attached for your reference.

---

### Post by stinkeye on 2012-11-14
> **gerowen said:**
> The "Disk Utility" has been updated to fit in with Gnome3/Unity and is now just called "Disks".  Just open it, highlight the partition you want to modify, click the little gear icon under it, and click "Edit Filesystem Label".  A screenshot is attached for your reference.

Don't have those options for my my usb stick or mp3 player...both fat formatted.

---

### Post by gerowen on 2012-11-14
> **stinkeye said:**
> Don't have those options for my my usb stick or mp3 player...both fat formatted.

Try ensuring that the partition is unmounted, just in case.

You could also try GParted, it seems to be the gold standard for disk management.

You could also try using mlabel.  I've never done it myself, but found this with Google.
[http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)

---

### Post by NikTh on 2012-11-14
Hi,

Try to set a label with mkfs.vfat 
**[COLOR=Red]Attention[/COLOR]** **this will destroy all of your data** . So if you have access , [SIZE=3]**backup first.**[/SIZE] 

```
sudo mkfs.vfat -n <label here> /dev/sdXX
```replace XX with the letter and number of the partition. 

Partition should be unmounted. 

Thanks

---

### Post by stinkeye on 2012-11-14
> **gerowen said:**
> Try ensuring that the partition is unmounted, just in case.

You could also try GParted, it seems to be the gold standard for disk management.

You could also try using mlabel.  I've never done it myself, but found this with Google.
[http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/](http://embraceubuntu.com/2006/03/01/editing-fat32-partition-labels-using-mtools/)
Thanks for the info.
I just booted into my Precise install and changing the label works 
in Disk utility.
Must be a problem with the the new "Disks".

---

