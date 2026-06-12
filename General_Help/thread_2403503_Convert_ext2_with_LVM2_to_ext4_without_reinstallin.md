---
title: "Convert ext2 with LVM2 to ext4 without reinstalling Ubuntu 18.04 64 bit operating sys"
date: 2018-10-12
forum: General Help
---

### Post by steveparbkk on 2018-10-12
Hi,

Dropbox is forcing me to covert my ext2 disk to ext4, otherwise it will no longer be supported.

This is my disk at the moment

[IMG]https://image.ibb.co/fGXBdp/Screenshot-from-2018-10-12-17-31-25.png[/IMG]

I'd like to convert sda2 and sda3 both to ext4 without compromising the data (home directory) in sda3.

I found [https://www.howtoforge.com/tutorial/migrate-ext2-ext3-filesystem-to-ext4/]("https://www.howtoforge.com/tutorial/migrate-ext2-ext3-filesystem-to-ext4/"), but that doesn't address the LVM2 issue.

Any thoughts gratefully considered.

---

### Post by Dennis N on 2018-10-12
As to the LVM question, gparted can't show you how the LV (logical volume) for your OS is formatted. If it was created by the installer, it is most probably ext4 already. Use:
```
lsblk -o name,fstype 
```
to check.

---

### Post by steveparbkk on 2018-10-12
Thanks for your prompt reply.  Looks like it may be ext4:-

[IMG]https://image.ibb.co/gvQpyp/Screenshot-from-2018-10-12-18-20-41-pix.png[/IMG]

---

### Post by Dennis N on 2018-10-12
Correct. **ubuntu--vg-root** is where your OS is installed and it has an ext4 file system.

---

### Post by steveparbkk on 2018-10-17
Thanks for your input, Dennis N, it has advanced my understand of the task at hand.  I've been giving my challenge a little more consideration.  It is clear that Dropbox doesn't like my LVM partition and therefore, probably the easiest way to accommodate Dropbox is to shrink my LVM partition and create another one, of, say, 20GB which i shall use exclusively for Dropbox.  The question is how to achieve that.  I've been looking at the LVM partition:

[IMG]https://image.ibb.co/jLwfff/Screenshot-from-2018-10-17-18-18-41.png[/IMG]

This indicates that sda3 is 3TB in size, so my idea was to reduce that by approximately 20GB and then create a new partition outside of the LVM and format it as ext4, presumably as sda4.  I'm not sure if that is possible.

[IMG]https://image.ibb.co/dbkFff/Screenshot-from-2018-10-17-18-27-54.png[/IMG]

[IMG]https://image.ibb.co/m56tY0/Screenshot-from-2018-10-17-18-29-34.png[/IMG]

This appears to suggest that I have almost 2TB of unused space.  The question is what is the easiest way to sequestrate about 20GB of that unused space to create another partition outside the LVM?

Any insights would be gratefull considered.

---

### Post by Dennis N on 2018-10-17
> so my idea was to reduce that by approximately 20GB and then create a new partition outside of the LVM and format it as ext4, presumably as sda4. I'm not sure if that is possible.
I'd bet it's possible, but I've never had to shrink an LVM physical partition that was already part of a volume group, so don't want to suggest steps that I've never tried. I found possibly relevant items with Google that may help. There are quite a few, but here are two:

[https://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume](https://askubuntu.com/questions/196125/how-can-i-resize-an-lvm-partition-i-e-physical-volume)
[http://www.tutorialspoint.com/unix_commands/pvresize.htm](http://www.tutorialspoint.com/unix_commands/pvresize.htm)

Just wondering: system-config-lvm (mentioned in first link discussion) doesn't seem to be in the ubuntu 18.04 repos any longer, but it's display is in your post. Is it part of Disks now?

also see in terminal: **man pvresize**

---

### Post by steveparbkk on 2018-10-21
Thanks....   I also found:

[https://unix.stackexchange.com/questions/67702/how-to-reduce-volume-group-size-in-lvm](https://unix.stackexchange.com/questions/67702/how-to-reduce-volume-group-size-in-lvm)

This has achieved something, but not the desired result, yet.  As I don't have much time now, I shall have to leave it for later, but it is clear that the amount of free space has been shrunk, although I can't see any unallocated space to create a new partition in, as yet.

[IMG]https://image.ibb.co/ibWe0f/Screenshot-from-2018-10-22-05-04-27.png[/IMG]

---

### Post by steveparbkk on 2018-10-23
Well, pvresize resulted in some progress, although as the following image shows, not yet success:

[IMG]https://image.ibb.co/bH64oA/Screenshot-from-2018-10-23-16-13-33.png[/IMG]

I now have 294 GB of unallocated space, but the problem is that it is still contained within the LVM partition and thus unavailable for use outside of the LVM.  So, now I just need to shrink the LVM container and in the process transfer the unallocated space outside the LVM.

---

