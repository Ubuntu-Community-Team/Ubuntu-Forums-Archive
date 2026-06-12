---
title: "Best 1:1 Disc copy method from pc1 to pc2?"
date: 2020-07-04
forum: General Help
---

### Post by ProDigit on 2020-07-04
Best options for 1:1 copying a boot HDD from pc1, to the boot hdd from pc2?
Identical drive sizes, needing identical settings.

I have options of ssh, or USB.
Problems arise when trying to copy a drive in use, so,
It's been suggested to use dd from a live USB, on the source PC drive, to an image on the USB drive, and overwrite the destination drive with the image on the drive.
Would this be the quickest option?

---

### Post by VMC on 2020-07-05
I use Macirum Reclect to clone from one HD to another.

Clonezilla is goog also if they are exactly the same size.

---

### Post by uninvolved on 2020-07-05
I use Acronis True Image. Clonezilla works if the new drive is as large - or larger - than the source drive. There are workarounds so that you can move your data to smaller drives, as well.

If the new drive is smaller than the old one, [see here]("https://www.ubackup.com/articles/clonezilla-clone-larger-disk-to-smaller-disk-4348.html") for more info about how to do that with Clonezilla.

---

### Post by sudodus on 2020-07-05
It is probably easiest to create an image in an external drive, move that drive to the other computer, and restore from the image in that drive into the internal drive. That way you will also get an image that can be used for backup purposes.

Cloning with dd is straight-forward, but risky, because there is no final checkpoint. dd does what you tell it to do without any question, even if you tell it to wipe the family pictures. So if you want the cloning method, it is better to use another tool, for example Disks alias gnome-disks.

But I prefer Clonezilla. It is smart enough to copy only the used blocks in the file systems, and skip the free blocks. This means that it will work faster, and the image will be smaller compared to crude cloning.

There are more details at this link: [Create bootable backup system image](https://askubuntu.com/questions/1255461/create-bootable-backup-system-image/), where one answer describes using Disks, and one answer (mine) describes using Clonezilla.

---

### Post by The Cog on 2020-07-05
Using image files would be the first thing that came to my mind, but if you don't have the spare capacity, you can always just stream the contents across the network.
I am assuming that the boot drive is /dev/sdx at both ends - make sure you know the right device IDs at both ends or you might trash the wrong drives!
See the section DATA TRANSFER in "man netcat".
On the recieving PC, listen for a connection and write to the disk:
**Edit**: sudodus points out that my original commands won't work because of sudo redirection. Below are corrected commands
```
sudo -i
nc -l 1234 > /dev/sdx
exit
```
Then on the sending end, read the disk and send to the receiver (I assume address 1.2.3.4):
```
sudo -i
nc -N 1.2.3.4 1234 < /dev/sdx
exit
```

---

### Post by sudodus on 2020-07-05
Thanks The Cog,

Great netcat method,  when there is no spare capacity to store an image file :-)

- **I tested and it works, when using nc of Ubuntu**.

- I tested also with nc of [FONT=Courier New]**debian-live-10.4.0-amd64-standard.iso**[/FONT] on the listening / receiving side, and it did not work. So the implementation of nc makes a difference.

- When we use this method, we must realize that it is **risky** in the same way as cloning with dd: There is no final checkpoint, so please check and double-check that the target device is the correct one, and the target computer is the correct one, before you start the process. Otherwise you might overwrite important data.

---

### Post by HermanAB on 2020-07-05
I've done the above many times in the past.  You can also pipe netcat through zip if your network is slow.

After a copy like that expect to have issues with UUIDs and MAC addresses, so there is a little bit of cleaup to do to get the new machine to boot.

---

### Post by SeijiSensei on 2020-07-05
I used ddrescue (from the gddrescue package) to clone two 512 GB laptop drives to identically sized SSDs.  Worked like a charm.  In my case, though, I connected the target with a [SATA to USB device]("https://www.newegg.com/vantec-cb-isatau2-usb-to-ide-sata/p/N82E16812232002") and booted from a USB boot drive I created with the tools in Ubuntu.  I would never try to clone a mounted drive.

---

### Post by TheFu on 2020-07-05
There are many ways to clone.  dd, ddrescue, fsarchiver, clonezilla, and because everything is a file we can use methods like nc or ssh or even bash network connections. Bash has a built-in nc on later versions.  Cloning implies a bit-for-bit copy. This is highly inefficient unless the HDD is mostly full.  Copying bits that aren't actually being used is wasteful.

if you don't need the grub stuff in specific places (legacy boot), then using rsync would be much more efficient.  rsync only gets real files and ignores empty space unlike most cloning methods.  But rsync works at the file level so the file system and lower levels have to be created some other way.  But with the rsync, some manual updates to the fstab will be needed.  rsync would be the fastest method, by far, but only if you can create partitions, file systems and modify the fstab quickly.  Those things are just a few minutes of effort total when you know how to do each correctly.

Doubt all this hand-waving is helpful.  Pick the specific way you want to go.

Of course, if you have a dual-dock with a cloning feature and don't mind letting it run overnight, that is the easiest solution. Dual-docks are about $30 and cloning is about 5% of the useful reasons to have one.

---

### Post by kurt18947 on 2020-07-05
I needed to copy a small partition and used Disks. 'Create a disk image' to a flash drive then 'Restore a disk image'. Worked fine. I don't know if the image created includes empty space or not.

Edit: it looks like Disks creates a 1:1 image so pretty wasteful if a partition is large and mostly empty. I guess you could resize(shrink) the partition, create the image, restore the partition at destination and resize again. Disks is probably not the correct tool in this case. I have had pretty decent luck resizing partitions and having them boot with no problems.

---

### Post by TheFu on 2020-07-05
fsarchiver does this larger to smaller partition move. it understands a few file system types, so it can be very smart for those. Not so smart about other file systems but no worse than dd.

Downside for all image-based clones is the source must be unused during the imaging, which usually means downtime to avoid corrupted images.  Of course volume managers that support real snapshots can can avoid that problem.

---

