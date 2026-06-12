---
title: "Shrinking Home VHD?"
date: 2007-06-25
forum: General Help
---

### Post by callit on 2007-06-25
Here's an interesting one.  My /home .vhd is shrinking.  Last night it shrunk to about 9MB free space.  I rebooted into windows, and increased the size to about 15GB using the tool recommended in the guide.  Today, it happened again.  For some reason, I couldn't download new videos in Democracy.  Checked my /home folder - only 12MB free.

Any thoughts on why my vhd is shrinking and how to stop it?  It's only happening on my /home disk, not my system or swap.

---

### Post by tuxcantfly on 2007-06-26
What I'd do is make a new loopmounted partition of desired size, copy over the contents of /home into it, boot into windows, delete your existing home, and replace it with the new one. Boot into your Ubuntu install created by Wubi, then open a terminal, and enter these commands to create a new home loopmounted partition (I assume you want 10 GB; adjust line 2 accordingly):

```
cd /media/host/wubi/disks
sudo dd if=/dev/zero of=newhome.virtual.disk bs=1000 count=0 seek=$[1000*1000*10]
sudo mkfs.ext3 -f newhome.virtual.disk
sudo mkdir /media/newhome
sudo mount -o loop ./newhome.virtual.disk /media/newhome
sudo cp -r /home/* /media/newhome
sudo umount /media/newhome
sudo rm -r /media/newhome
```

Now reboot into Windows, rename C:\wubi\home.virtual.disk to oldhome.virtual.disk (keep it as a backup in case something screws up), and rename newhome.virtual.disk to home.virtual.disk, reboot, and all should work...

---

### Post by callit on 2007-06-27
thanks for the info.  The drive apparently shrunk once (or maybe I just wasn't paying attention to the installer and only created a 100MB /home folder?  Doesn't seem like something I'd do, but makes more sense than a shrinking file), and there's apparently 10GB in use in a hidden file somewhere in /home that I'll have to track down (it transfered over to the new virtual disk).

I followed your instructions and encountered two issues:
On line 3 you use the -f switch without providing an argument.  I eliminated the -f and it seemed to work as expected.
Copying the files in that manner apparently changed the owner of them to root.  Once I rebooted I couldn't log back into the gui, but it was a quick fix:
Switch to a console and sudo chown -R user /home/user (in case anyone else has similar issues)

I wanted to increase the size of my home disk anyway, so this killed two birds with one stone.  I was a little weary of the windows utility mentioned in the guide, but it seemed to do the job okay the first time around.

as a follow up, any suggestions on tracking down the file(s) eating up 10GB in my home folder? a find -size yielded only one file over 10MB

---

### Post by ago on 2007-06-27
> **callit said:**
> Here's an interesting one.  My /home .vhd is shrinking.  Last night it shrunk to about 9MB free space.  I rebooted into windows, and increased the size to about 15GB using the tool recommended in the guide.  Today, it happened again.  For some reason, I couldn't download new videos in Democracy.  Checked my /home folder - only 12MB free.

Any thoughts on why my vhd is shrinking and how to stop it?  It's only happening on my /home disk, not my system or swap.

When you reinstall, if you backup home, the old file will be reused as is. So if you had 9MB free, you will end up with 9MB free. If you have no important setting, just reinstall without backing up home and a new virtual drive will be created.

---

