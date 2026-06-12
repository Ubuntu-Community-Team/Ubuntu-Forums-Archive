---
title: "hibernate: where to define swap partition"
date: 2006-10-07
forum: General Help
---

### Post by RikoW on 2006-10-07
Hi all,

I noticed, that my laptop does not hibernate anymore. I get an error message saying "Cannot find swap device!" I know, that it used to work and I know that swap is turned on.

Not too long ago, I changed the hard disc of the laptop and in the process also adjusted the partions, but otherwise just copied the partion content from the old disc to the new one (editing fstab of course).
So I assume, somewhere, when Ubuntu was installed, a hibernate script was configured which has the swap partion hard coded inside. After changing the disc layout, the swap partition is a different one.

Anybody know, where I can fix that?

Thanks and cheers,
                 Riko

---

### Post by RikoW on 2006-10-08
ok, here's what you need to do to get hibernate working again, after changing  the partition layout of your hd, or if the partition number of the swap partitionhas changed for whatever reason. I had to apply the things suggested in these two threads:

[http://www.ubuntuforums.org/showthread.php?t=196965]("http://www.ubuntuforums.org/showthread.php?t=196965")
[https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/55535]("https://launchpad.net/distros/ubuntu/+source/acpi-support/+bug/55535")

My swap was on /dev/hda6 and is now on /dev/hda7, so you need to edit:

```
sudo gedit /etc/mkinitramfs/conf.d/resume
```

and change to entry there to:

```
RESUME=/dev/hda7
```

then run:

```
sudo dpkg-reconfigure initramfs-tools
```

That was the recommendation of the first thread, but apparentely, not enough. Finding the second one, I did:

```
sudo gedit /etc/mkinitramfs/initramfs.conf
```

find the entry RESUME and change to the correct swap partition

```

RESUME=/dev/hda7

```

then run:

```
sudo update-initramfs -u

```

After a reboot of the machine, hibernate should be working again.
I suspect, the last "update-initramfs" call is probably enough, but I'm just guessing here.

Hope, this might help someone, too :)

        Cheers,

                  Riko

---

### Post by jatatar on 2006-12-15
This was not a good solution, did not have the files shown in this post...

First, you should look in file /etc/fstab, make sure the swap entry is not commented out and that it points to the right partition.

Save file...reboot...try to hibernate again

---

### Post by RikoW on 2006-12-15
Of course, you need to make sure, that fstab mounts the right partition as swap.

But I assume, that did the trick for you because before you set-up the initial ramdisk correctly, as described above.

I guess, to be complete, I should have added "update fstab acoordingly" in the previous post.

Cheers,

                 Riko

---

### Post by zgornel on 2006-12-15
Do a ```
free -m
``` and check is swap is actually used.

---

### Post by jazzgossen on 2008-03-08
Just a comment to this solution (using 7.10).

After I changed my swap partition, I updated /etc/fstab but I forgot to run ```
mkswap /dev/sda7
``` (where /dev/sda7 is my new swap partition, of course). That's also important. The file to edit was /etc/initramfs-tools/initramfs.conf instead of /etc/mkinitramfs/conf.d/resume as mentioned in the first post. Also, I had no resume entry in the file /etc/mkinitramfs/initramfs.conf .

---

### Post by ethanay on 2008-05-20
actually, I think it is 

/etc/initramfs-tools/conf.d/resume

where you are supposed to define the location, at least in hardy

update the file with your real /dev/sdaX or /dev/hdaX swap device

and run
```
update-initramfs -u
```

sources:
[bug 66637]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/66637")
[bug 50437]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/50437")

also, to avoid any UUID errors, I believe you can update fstab by deleting any of the funky UUID stuff and using just the /dev/sdaX or /dev/hdaX pointer

---

