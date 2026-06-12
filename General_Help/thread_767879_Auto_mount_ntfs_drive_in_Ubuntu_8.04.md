---
title: "Auto mount ntfs drive in Ubuntu 8.04?"
date: 2008-04-26
forum: General Help
---

### Post by fuzzyl0g1c on 2008-04-26
So I used wubi to install Ubuntu 8.04 from vista, and it doesn't automatically mount a ntfs drive with music I need. I know how to manually mount it, but how do I set up to do this at boot? Thanks!

---

### Post by cold_fu5ion on 2008-04-26
Hi there,

Someone may have to correct this, but I just set up my NTFS drives to auto-mount by doing the following: (note this will allow NTFS write)

1: Open up Terminal (Applications - Accessories - Terminal) and type the following: ```
sudo fdisk -l
```

you will be asked for the root password (password you chose at setup) and will be presented with a list that looks similar to this:

```
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e4abf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2   *           1       38913   312568641    7  HPFS/NTFS

```

this tells us that the drive is 320GB and is located at /dev/sdb2, you will need to remember the location of the drive.

2: In terminal again, type
```
sudo gedit /etc/fstab
```

You will be presented with your fstab file, which basically tells Ubuntu where to mount the drives listed.

3: At the bottom of the fstab file paste the following:
```
/dev/sdb2       /media/wimpy ntfs-3g  defaults  0   0
```

You will need to adjust 2 things: the name /dev/sdb2 to the drive that is specific to your computer, and the name /media/wimpy. The name I chose "wimpy" the directory where the drive will be mounted. Save the file

4: to create the mount point, open Terminal and type:
```
sudo mkdir /media/wimpy
```

where "wimpy" matches the name you used in the fstab file.

5. To test that it works, type:

```
sudo mount -a
```

This will mount all the drives listed in the fstab file.
I think that you will then need to do a restart to notice the changes if you add more drives.

You can also change the drive name using:

```
sudo ntfslabel /dev/sdb3 wimpy
```

Although the drive has to be unmounted first.


Hope that helps.

---

### Post by MrMarc on 2008-07-26
Thank you! That sorted out one niggle for my install! :) Now my desktop wallpaper from my NTFS drive always displays on startup.

By the way I know this is irrelevant but how do I thank somebody for their post without actually posting a new message?

---

### Post by DagMan on 2008-07-26
You click on this thing that's located at the bottom right of their post [IMG]http://ubuntuforums.org/images/buttons/post_thanks.gif[/IMG]

---

### Post by MrMarc on 2008-07-26
Cool thanks for that, although the icon wasn't shown on cold_fu5ion's post! Oh well not to worry, thanks again! :)

---

### Post by VitaminBB on 2008-08-03
This is something im trying to do myself.

I have a drive in a usb enclosure that I plug into my laptop, it is formatted in NTFS and has my images and mp3s etc, if I can get Ubuntu to "see" it that would be a great setup.

Following the information above I did the fdisk-l and I cant see anything pointing to the NTFS drive, it is plugged in and Ubuntu sees the drive, just says it cant mount because its NTFS.

This is the info I get after typing sudo fdisk -l in terminal ...

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14264   114575548+  83  Linux
/dev/sda2           14265       14593     2642692+   5  Extended
/dev/sda5           14265       14593     2642661   82  Linux swap / Solaris

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdfb68f5d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       11300    90767218+   6  FAT16
/dev/sdc2           11301       14593    26451022+   f  W95 Ext'd (LBA)
/dev/sdc5           11301       14593    26450991    b  W95 FAT32

Any ideas?

---

### Post by VitaminBB on 2008-08-03
Ok somethings wrong here ...

I tried to follow the HOWTO setup here ... [http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

But I cant find the NTFS device when im in terminal anywhere, im lost *L*

I can see the NTFS drive under "Places" but when I click on it I am told "unable to mount volume 'Osmosis' " (thats the name of the drive.

Now, it gets even more confusing, on this same external drive I have a small fat16 drive and something I have done has forced this drive to appear on the desktop even when the external drive is unplugged and when the drive is plugged in I see two 'PS3' volumes (the fat16 partition on the NTFS external drive).

Im fricking confused.

I want to get my Ubuntu to recognize NTFS so I can grab files and explore on that volume, I also want to get Ubuntu to stop mounting the fat16 volume on the drive when I unlug the external drive.

Anyone?

---

### Post by drs305 on 2008-08-03
I've written a tutorial on how to use pysdm, a gui-based app to edit fstab. It got a little long so I put a "3 Minute Guide" at the top of it. If you are interested, you can get to it via the link in my signature.

---

### Post by VitaminBB on 2008-08-03
Right on, first thing to report, it worked! I can now see my files, thanks for that ...

There is one problem though, the devices seem to be breeding ...

I am getting multiples of the volumes that arent disappearing when I disconnect and theres no option i see to unmount these phantom volumes ...

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot.jpg[/IMG]

---

### Post by drs305 on 2008-08-04
> **VitaminBB said:**
> Right on, first thing to report, it worked! I can now see my files, thanks for that ...
I am getting multiples of the volumes that arent disappearing when I disconnect and theres no option i see to unmount these phantom volumes ...

That is interesting. I can offer a few suggestions although they are not necessarily 'fixes':

1. If you run "sudo umount -a" do the icons disappear? Then "sudo mount -a" and see if only one reappears.

2. You could change the mount point to something other than /media/XXX. Devices mounted in /media display on the desktop by default. Those on /mnt or anywhere else won't by default.

3. You can run this command to hide mounted volumes. 
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'false'

```

Change the value to 'true' to restore them to the desktop.

---

### Post by Sonicgoo on 2008-09-19
Thanks I'm always forgetting the simple stuff this thread was most helpful

---

### Post by Up2Late on 2008-10-24
OK, I must say this thread is a little disturbing to me.

I'm putting together a new system, and thought I'd run Ubuntu on it.  Thought I'd take a quick look to see if Ubuntu would read my external NTFS drives.

Answer, yes it will, but it won't automount without a little tweaking.

I've been getting crap for the last few releases that Ubuntu is just as straight forward as Windows for a new user, but this is sounding to be untrue.

Will 8.10 fix this issue?  How about networking with Windows?

I used to have time to read through forums and figure stuff out, but with 3 kids, work, and a house to take care of, I don't have time anymore.

---

### Post by jerome1232 on 2008-10-24
If the ntfs drive is present when you install the os, and you give it a mount point, it will be mounted just fine. 

All that had to be done here was add an fstab entry for the drive so that it will be mounted at boot, rather than mounting it manually when you need the disk. Windows can't read any files systems other than ntfs (it's own) and fat so no this isn't something easily done there.

Networking is easy to, alot of people go with samba to network with windows, I like to use scp personally.

---

### Post by Up2Late on 2008-10-24
"Windows can't read any files systems other than ntfs (it's own) and fat so no this isn't something easily done there."

Good point.

This computer's main purpose is going to be an HTPC attatch to my Samsung LCD via HDMI, so I guess I won't be doing anything too complicated.

FYI: just tried 8.10 rc  live cd (64-Bit)on my wife's hp dv6000... no wifi.  Personally, I'll be plugging into a jack, so it's not an issue.

also, no problems detecting my windows network, and played h.264 HD files smoothly (Core 2 Duo T7200) after installing plugins.

---

### Post by 4hp007 on 2010-06-26
Thanks alot worked well for me. Atleast now i dont have to mount again and again the vmware disk. THANKS

---

